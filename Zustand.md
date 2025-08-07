https://zustand-demo.pmnd.rs/

é uma lib de gerenciamento de estado global na aplicacao e tal, ai ela ajuda a fazer com que voce consiga acessar teus dados de onde quiser globalmente e tal, muito semelhante ao que outras ja fazem, como redux, contextAPI e etc

vidoe que vi
https://www.youtube.com/watch?v=_ngCLZ5Iz-0&t=924s

aq tudo que aprendi

```js
import { create } from "zustand";

type Note = {
  id: string;
  text: string;
};

type ListState = {
  notes: Note[];
  addNote: (note: string) => void;
  removeNote: (id: string) => void;
};

export const useListStore = create<ListState>((set) => ({
  notes: [],
  addNote: (note: string) => {
    set((state) => ({
      notes: [
        ...state.notes,
        {
          id: crypto.randomUUID(),
          text: note,
        },
      ],
    }));
  },
  removeNote: (id: string) => {
    set((state) => ({
      notes: state.notes.filter((note) => note.id !== id),
    }));
  },
}));

```

```js
import { create } from "zustand";

type CounterStore = {
  count: number;
  increment: () => void;
  decrement: () => void;
  reset: () => void;
};

export const useCounterStore = create<CounterStore>((set) => ({
  count: 0,
  increment: () => {
    set((state) => ({ count: state.count + 1 }));
  },
  decrement: () => {
    set((state) => ({ count: state.count - 1 }));
  },
  reset: () => {
    set({ count: 0 });
  },
}));

```

```js
import { useState } from "react";
import { useListStore } from "./store/list";

export const List = () => {
  const { addNote, notes, removeNote } = useListStore((state) => state);
  const [note, setNote] = useState("");

  return (
    <div className="min-h-screen flex items-center flex-col justify-center bg-gradient-to-br from-slate-100 to-slate-300 p-4">
      <div className="bg-white rounded-2xl shadow-2xl p-8 w-full max-w-sm text-center">
        <h1 className="text-3xl font-bold text-gray-800 mb-4">List</h1>
        <input
          className="w-full p-3 mb-4 border rounded-lg focus:ring-2 focus:ring-blue-500 focus:outline-none transition"
          type="text"
          name="note"
          id="note"
          placeholder="Add a new note..."
          onChange={(e) => setNote(e.target.value)}
          value={note}
        />
        <button
          onClick={() => addNote(note)}
          className="w-full bg-blue-500 hover:bg-blue-600 text-white px-5 py-2 rounded-xl transition"
        >
          Submit
        </button>
      </div>

      <ul className="mt-6 space-y-3 w-full max-w-sm">
        {notes.length > 0 &&
          notes.map((note) => (
            <li
              key={note.id}
              className="bg-white p-4 rounded-lg shadow-md text-gray-800 text-left"
            >
              <span>{note.text}</span>
              <button
                onClick={() => removeNote(note.id)}
                className="ml-4 text-red-500 hover:text-red-700 transition"
              >
                Delete
              </button>
            </li>
          ))}
      </ul>
    </div>
  );
};

```

```tsx
import { useEffect } from "react";
import { useCounterStore } from "./store";

const logCount = () => {
  // print do estado, nao atualizado, ou seja, nao recria a tela
  const count = useCounterStore.getState().count;
  console.log(`Current count: ${count}`);
};

export function App() {
  // uma funcao que pega o estado atualizado, mas faz reiniciar a tela
  const count = useCounterStore((state) => state.count);
  const increment = useCounterStore((state) => state.increment);
  const decrement = useCounterStore((state) => state.decrement);
  const reset = useCounterStore((state) => state.reset);

  useEffect(() => {
    logCount();
  });

  return (
    <div className="min-h-screen flex flex-col items-center justify-center bg-gradient-to-br from-slate-100 to-slate-300 p-4">
      <div className="bg-white rounded-2xl shadow-2xl p-8 w-full max-w-sm text-center">
        <h1 className="text-3xl font-bold text-gray-800 mb-4">
          Simple Counter
        </h1>
        <p className="text-6xl font-extrabold text-blue-500 mb-6">{count}</p>

        <div className="flex justify-center gap-4">
          <button
            onClick={decrement}
            className="bg-red-500 hover:bg-red-600 text-white px-5 py-2 rounded-xl transition"
          >
            -
          </button>

          <button
            onClick={reset}
            className="bg-gray-300 hover:bg-gray-400 text-gray-800 px-5 py-2 rounded-xl transition"
          >
            Reset
          </button>

          <button
            onClick={increment}
            className="bg-green-500 hover:bg-green-600 text-white px-5 py-2 rounded-xl transition"
          >
            +
          </button>
        </div>
      </div>
    </div>
  );
}

```


