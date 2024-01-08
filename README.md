# localStorageSignal
```js
import { signal,useSignal, effect,useSignalEffect } from "@preact/signals-react";

export const storageSignal = (key, initialValue) => {
  const value = signal(parsedValue(key) || initialValue);

  effect(() => {
    localStorage.setItem(key, value.value);
  });

  return value;
};

export const useStorageSignal = (key, initialValue) => {
  const value = useSignal(parsedValue(key) || initialValue);

  useSignalEffect(() => {
    localStorage.setItem(key, value.value);
  });

  return value;
};

function parsedValue(key){
  const storedValue = localStorage.getItem(key);

  try {
    return JSON.parse(storedValue);
  } catch (error) {
    // If parsing fails, return the original value as is
    return storedValue;
  }
}
```
