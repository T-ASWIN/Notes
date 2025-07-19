
---

### ✅ How React Handles DOM Updates

1. **Virtual DOM & Snapshot Comparison**
   React uses a **Virtual DOM** to improve performance. Whenever there is a change in state or props, React:

   * Creates a **new virtual DOM snapshot**.
   * **Compares** it with the **previous snapshot** to detect changes.
   * Determines **what part of the real DOM** needs to be updated.

2. **Component Rendering Behavior**

   * If a component is **not affected by the update** (its props/state haven’t changed):

     * The **component function is not re-executed**.
     * React **reuses the last rendered output**.
   * If a component **is affected by the update**:

     * Its **function is re-executed** to get new JSX.
     * The new output is compared via the virtual DOM diffing process.

3. **Efficient DOM Updates**

   * React builds a **component tree** representing the UI.
   * It identifies the **minimal set of changes** by comparing the new virtual DOM with the old one.
   * Then, it **efficiently updates the real DOM** — only the parts that changed — without reloading the whole page.

---

