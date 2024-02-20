#  React - Introduction to Rendering Lists

## Setup 
Before we begin writing code, let's setup the project and install all necesarry packages.
Open a new Terminal window and do the following steps:

1. Go to `calab` directory:
    ```
    cd calab
    ```
2. Install npm packages:
    ```
    npm install
    ```
3. Start the application:
    ```
    npm run dev
    ```
    You should see the development server being started:
    [![Started](resources/started.png)]() 

    If you open the `Local` URL in a new browser tab, you should see the follwoing:
    [![Initial](resources/initial_screen.png)]()    


## Steps 

1. Make use of React hook useState to keep track of list of fruits we want to render.
    -   Open `App.jsx` file.
    -   Import `useState` react hook, at the top of the file.
        ```
        import React, {useState} from 'react';
        ```
    -   Inside App() function, just before the `return` statement, declare the state variable. Set list of following values as default list of fruits `['Apple','Banana','Orange','Grapes','Strawberry']`.
        ```
        const [fruits, setFruits] = useState(['Apple','Banana','Orange','Grapes','Strawberry']);
        ```

2. Now tha fruits list is set, let's render it on a screen. 

    -   First, Open `App.jsx` file and change text in `<h1>` to "List of Fruits".

    -   Then after the `<h1>` element, let's insert the unordered list by creating `<ul>` element.
        ```JSX
        <ul>
        </ul>
        ```

3. Inside `<ul>` element map over the list of fruits and rendering each fruit as a list item `<li>`.
    ```JSX
    {fruits.map((fruit, index) => (
        <li key={index}>{fruit}</li>
    ))}
    ```


### Refactor. Make Code more clean and reusable

1. Create a new directory called `components` inside `calabs/src`.

2. Create a List component.
    -   Inside `calab/src/components` create a new file called `List.jsx`.
    -   Inside `List.jsx` add the following code:
        ```
        function List({fruits}) {
            return (
            <ul>
            </ul>
            )
        }
        export default List
        ```

3. Create a ListItem component.
    -   Inside `calab/src/components` create a new file called `ListItem.jsx`.
    -   Make `ListItem.jsx` to return the `<li>` element.:
        ```
        function ListItem({id, fruit}) {
            return (
                <li key={id}>{fruit}</li>
            )
        }
        export default ListItem
        ```

4. Go back to `List.jsx` and make use of `ListItem.jsx`
    -   Inside `<ul>` add the following code that maps each fruit that is passed into the `List` component via `props` to the `ListItem` component.
    - Import `ListItem` component.

        ```
        import ListItem from "./ListItem"
        ```
    -   Render it.
        ```  
        {fruits.map((fruit, index) => (
            <ListItem key={index} fruit={fruit}></ListItem>
        ))} 
        ```

5. Import `List.jsx` into `App.jsx` and use it.
    -   Import `List.jsx` component.
        ```
        import List from './components/List'
        ```
    -   Just below `<h1>` insert `List.jsx` component and pass fruits list as a prop.
        ```
        <List fruits={fruits}></List>
        ```

If you followed the steps correctly you should see the following when you run your react application:
[![Result](resources/result1.png)]()  
