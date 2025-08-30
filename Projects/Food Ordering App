function cartReducer(state, action) {
  // Checks if the action is to add an item
  if (action.type === "ADD_ITEM") {
    // Finds the index of the item in the cart (if it already exists)
    const existingCartItemIndex = state.items.findIndex(
      (item) => item.id === action.item.id
    );
    // Makes a copy of the current items array
    const updatedItems = [...state.items];

    // If the item is already in the cart
    if (existingCartItemIndex > -1) {
      // Gets the existing item
      const existingItem = state.items[existingCartItemIndex];
      // Creates a new item object with increased quantity
      const updatedItem = {
        ...existingItem,
        quantity: existingItem.quantity + 1,
      };
      // Updates the item in the copied array
      updatedItems[existingCartItemIndex] = updatedItem;
    } else {
      // If the item is not in the cart, adds it with quantity 1
      updatedItems.push({ ...action.item, quantity: 1 });
    }
    // Returns the new state with the updated items array
    return { ...state, items: updatedItems };
  }

  // Checks if the action is to remove an item (not implemented yet)
  if (action.type === "REMOVE_ITEM") {
  }
  // Returns the current state if no action matches
  return state;
}
