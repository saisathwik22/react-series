# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

# A Documentation about the project

- import following hooks
  useState - for state management
  useCallback - memoizing functions
  useEffect - for side effects
  useRef - for referencing DOM elements

- define function app and initialize following states
  length - state variable to store length of password (default 8)
  numberAllowed - bool to indicate if numbers are allowed (default false)
  charAllowed - bool to indicate if characters are allowed (default false)
  password - state to store generated password.

- use "useRef" hook to create a reference to access the password input element in DOM. Now, this reference is used to copy the password.

- define passwordGenerator function
  Use callback function to memoize the function.
  Initialize empty string to build the password "pass".
  Start with base string with uppercase and lowercase letters.
  If numbers and characters are allowed, append them to the pass string.
  Use for loop to pick random chars from string and append them to pass.
  Update password state with generated password that is setPassword(pass) where setPassword is the state we defined at the beginning.

- define copyPasswordToClipboard function
  Use callback function to memoize the function.
  Select the text in password input field using the reference we created using useRef hook.
  Ensure entire text is selected.
  Copy the password to clipboard.

- functionality of "window.navigator.clipboard.writeText(password)"
  'window' object represents the browser's window and provide access to various browser related APIs and properties.
  'navigator' property of window object provides info about user's browser and OS as well as some web-related APIs.
  'clipboard' is an interface for interaction, its part of clipboard API which allows web-apps to read from or write to system clipboard.
  'writeText' method to write text to the clipboard, returns a promise that resolves once text has been successfully written to clipboard.

  The password variable is passed to writeText, writeText attempts to write it to clipboard, if successfull promise returned gets resolved.

- Generate password on state change using effect hook
  Use 'useEffect' to generate password whenever length, numberAllowed, charAllowed, or passwordGenerator change.
  This ensures password is regenerated with updated settings.

- Render the User Interface using return
  Create a 'div' for the password generator app with appropriate styling.
  Display a header for the application.
  Create a flex container to hold the password input field and the copy button.
  Input field (readOnly, referenced by passwordRef) displays the generated password.
  Button to trigger the copyPasswordToClipboard function.
  Create UI elements to adjust password settings.
  A range input to set the password length, updating the length state on change.
  Checkboxes to toggle the inclusion of numbers and special characters, updating numberAllowed and charAllowed states on change.
  Labels to display current settings.

- Export the 'App' component as the default export of the module.

# Quick Explanation about hooks used in this project:

NOTE: refer -[React](react.dev) official documentation for detailed explanation.

useState Hook:

- allows you to add state to functional components.
- It returns an array containing two elements, current state value and a function that updates the state.
  Syntax: const [state, setState] = useState(initialState);
  where,
  state - the current state value.
  setState - a function that allows you to update the state.
  initialState - initial value of state.

useCallback Hook:

- to memoize functions, ensuring they are re-created only when their dependencies change. This improves performance.
  Syntax:
  const memoizedCallback = useCallback(() => {
  // Your callback function
  }, [dependencies]);
  memoizedCallback: The memoized version of the callback function.
  dependencies: An array of dependencies. The callback is only re-created if one of these dependencies changes.
  When to use?
- to prevent unnecessary re-renders of components without any change in dependencies.
- performance optimization.

useEffect Hook:

- to handle side effects in functional components.
- Side effects are operations that affect something outside the scope of the function being executed.
  Syntax:
  useEffect(() => {
  // Your side effect code here
  return () => {
  // Cleanup code here
  };
  }, [dependencies]);
  Effect Function: The first argument to useEffect is the function containing your side effect code.
  Cleanup Function: This optional function is returned from the effect function and is used for cleaning up resources to avoid memory leaks.
  Dependencies: The second argument is an array of dependencies that determine when the effect should re-run. If the dependencies change, the effect will re-run.

useRef Hook:

- to create mutable references object whose ".current" property is initialized to passed argument(initial state).
  Syntax: const refContainer = useRef(initialValue);
  refContainer: The object returned by useRef. It has a .current property that holds the mutable value.
  initialValue: Optional. Initial value for .current. Can be null or any other value.

When to use?

- referencing DOM elements.
- storing previous values.
- keeping values between renders.
- avoiding re-renders with '.current'.
