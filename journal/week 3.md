# Week 2

- [ ] Defining a ThemeContext using the createContext function from React.
- [ ] Interface ThemeContextType that defines the mode and setMode properties.
- [ ] The ThemeProvider component is also defined, which takes in children as a prop and returns a ThemeContext.Provider with the value set to an object containing the mode and setMode properties.

## ThemeProvider : globally accessible theme state

The ThemeProvider function is a React component that provides a theme context to its children. It takes a single prop called children, which is a React node representing the child elements that will be wrapped by the ThemeProvider. Inside the function, there are two state variables defined using the useState hook: mode and setMode. The mode variable is initialized to the string "light", and setMode is a function that can be used to update the mode variable.

## handleThemeChange : storing the theme state

The ThemeProvider function also defines a function called handleThemeChange. This function is used to toggle the theme between light and dark modes. It checks the current value of mode and updates it to the opposite value, and then adds or removes the appropriate CSS class from the documentElement to change the theme.

The ThemeProvider function uses the useEffect hook to call the handleThemeChange function whenever the mode variable changes. This ensures that the theme is updated whenever the user toggles it.

## UseTheme : retriving theme state

The useTheme function is a custom hook that can be used to access the theme context defined by the ThemeProvider. It uses the useContext hook to retrieve the context object, and then returns it. If the context object is undefined, it throws an error indicating that useTheme must be used within a ThemeProvider.

Overall, the [themeProvider.tsx](../context/ThemeProvider.tsx) file provides a way to manage a theme context in a React project using TypeScript. It defines a ThemeProvider component that can be used to wrap child components and provide them with access to the theme context, as well as a useTheme hook that can be used to retrieve the theme context within child components.
