# senthilnathan.js.org
onSortingChange: (newSorting) => {
            // Ensure sorting state only contains plain serializable objects
            const serializableSorting = newSorting.map(({ id, desc }) => ({
              id,
              desc,
            }));
            dispatch(setManualSorting(serializableSorting)); // Dispatch using the new action
          },
