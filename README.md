# senthilnathan.js.org
import { useReducer } from 'react';
import { createSlice } from '@reduxjs/toolkit'; 

// Create a slice with initial state, reducers, and actions for sorting
const sortingSlice = createSlice({
  name: 'sorting',
  initialState: (initialField = 'id', initialOrder = 'ASC') => ({
    sorting: [{ id: initialField, desc: initialOrder === 'DESC' }],
    field: initialField,
    order: initialOrder,
    initialField,
    initialOrder,
  }),
  reducers: {
    setSorting: (state, action) => {
      state.sorting = action.payload;
      state.field = action.payload.length ? action.payload[0].id : state.initialField;
      state.order = action.payload.length
        ? action.payload[0].desc
          ? 'DESC'
          : 'ASC'
        : state.initialOrder;
    },
  },
});

// Extract the action creator and reducer from the slice
export const { setSorting } = sortingSlice.actions;
const sortingReducer = sortingSlice.reducer;

// Custom hook using useReducer with the sorting slice
export function useSorting(initialField = 'id', initialOrder = 'ASC') {
  const initialState = sortingSlice.getInitialState(initialField, initialOrder);

  const [state, dispatch] = useReducer(sortingReducer, initialState);

  const onSortingChange = (newSorting) => {
    dispatch(setSorting(newSorting));
  };

  return {
    sorting: state.sorting,
    onSortingChange,
    order: state.order,
    field: state.field,
  };
}
