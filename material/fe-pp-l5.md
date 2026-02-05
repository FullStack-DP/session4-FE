
# React useState

## Part 1: Book Collection Manager

In this activity, you'll build a **Book Collection Manager** that demonstrates React's `useState` hook. The application will allow users to add and remove books from a collection. We'll build this in 4 iterations, starting with basic setup and progressively adding functionality and styling.


### Iteration 0: Basic Setup

1. Open your `VS Code` editor in the `week4` directory.
2. Create a new React project and start the development server. For full steps on creating a React project with `Vite`, refer to [these instructions](./vite.md). In brief, run:

   ```bash
   npx create-vite@latest week4-pp-part1 --template react
   cd week4-pp-part1
   npm install
   npm run dev
   ```

   - This will create a new React project named `week4-pp-part1` and start it.
   - **Note**: By default, Vite runs on port `5173`.  
   - When using Vite with React, it's recommended to use the `.jsx` extension for files containing JSX syntax. If a file contains only standard JavaScript, the `.js` extension is fine.

3. Clean up the default styles so they do not interfere with the lab:

  - In `src/index.css`, remove the default CSS (you can leave it empty).
  - In `src/App.css`, remove the default CSS (you can leave it empty).

4. Replace the contents of `src/App.jsx` and `src/App.css` with the code from **Iteration 0** below.

Create the foundation of your Book Collection Manager with basic HTML structure and minimal styling.

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function BookCollectionManager() {
  const [books, setBooks] = useState([]);

  return (
    <div className="app-container">
      <h1>Book Collection Manager</h1>
      <p>Welcome! Let's start building your book collection.</p>
    </div>
  );
}

export default BookCollectionManager;
```

#### `src/App.css`

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f5f5f5;
}

.app-container {
  max-width: 600px;
  margin: 40px auto;
  padding: 30px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.app-container h1 {
  color: #2c3e50;
  margin-bottom: 10px;
  font-size: 28px;
}

.app-container p {
  color: #7f8c8d;
  font-size: 16px;
}
```

**What you should see**: A centered card with the title "Book Collection Manager" and a welcome message.

### Iteration 1: Add Input Fields and State Management

Now add state variables for book title and author, along with input fields for users to enter book information.

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function BookCollectionManager() {
  const [books, setBooks] = useState([]);
  const [title, setTitle] = useState("");
  const [author, setAuthor] = useState("");

  // Handle input change for title
  function handleTitleChange(event) {
    setTitle(event.target.value);
  }

  // Handle input change for author
  function handleAuthorChange(event) {
    setAuthor(event.target.value);
  }

  return (
    <div className="app-container">
      <h1>Book Collection Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter book title..."
          value={title}
          onChange={handleTitleChange}
          className="input-field"
        />
        <input
          type="text"
          placeholder="Enter author name..."
          value={author}
          onChange={handleAuthorChange}
          className="input-field"
        />
      </div>
    </div>
  );
}

export default BookCollectionManager;
```

#### `src/App.css`

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f5f5f5;
}

.app-container {
  max-width: 600px;
  margin: 40px auto;
  padding: 30px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.app-container h1 {
  color: #2c3e50;
  margin-bottom: 20px;
  font-size: 28px;
}

.input-section {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 20px;
}

.input-field {
  padding: 12px 15px;
  font-size: 16px;
  border: 1px solid #bdc3c7;
  border-radius: 6px;
  transition: border-color 0.3s ease;
}

.input-field:focus {
  outline: none;
  border-color: #3498db;
  box-shadow: 0 0 5px rgba(52, 152, 219, 0.3);
}
```

**What you should see**: Two input fields where users can type the book title and author name. The fields should highlight with a blue border when focused.

### Iteration 2: Add the "Add Book" Button

Implement the `addBook` function and button to add books to the collection.

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function BookCollectionManager() {
  const [books, setBooks] = useState([]);
  const [title, setTitle] = useState("");
  const [author, setAuthor] = useState("");

  // Handle input change for title
  function handleTitleChange(event) {
    setTitle(event.target.value);
  }

  // Handle input change for author
  function handleAuthorChange(event) {
    setAuthor(event.target.value);
  }

  // Add a new book to the list
  function addBook() {
    if (title.trim() !== "" && author.trim() !== "") {
      setBooks((b) => [...b, { title, author }]);
      setTitle("");
      setAuthor(""); // Clear the input fields
    }
  }

  return (
    <div className="app-container">
      <h1>Book Collection Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter book title..."
          value={title}
          onChange={handleTitleChange}
          className="input-field"
        />
        <input
          type="text"
          placeholder="Enter author name..."
          value={author}
          onChange={handleAuthorChange}
          className="input-field"
        />
        <button onClick={addBook} className="add-button">
          Add Book
        </button>
      </div>
    </div>
  );
}

export default BookCollectionManager;
```

#### `src/App.css`

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f5f5f5;
}

.app-container {
  max-width: 600px;
  margin: 40px auto;
  padding: 30px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.app-container h1 {
  color: #2c3e50;
  margin-bottom: 20px;
  font-size: 28px;
}

.input-section {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 20px;
}

.input-field {
  padding: 12px 15px;
  font-size: 16px;
  border: 1px solid #bdc3c7;
  border-radius: 6px;
  transition: border-color 0.3s ease;
}

.input-field:focus {
  outline: none;
  border-color: #3498db;
  box-shadow: 0 0 5px rgba(52, 152, 219, 0.3);
}

.add-button {
  padding: 12px 20px;
  font-size: 16px;
  font-weight: 600;
  color: white;
  background-color: #27ae60;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.1s ease;
}

.add-button:hover {
  background-color: #229954;
}

.add-button:active {
  transform: scale(0.98);
}
```

**What you should see**: A green "Add Book" button below the input fields. When clicked, it should add the book to the collection (though we haven't displayed the list yet) and clear the input fields.


### Iteration 3: Display the Book List and Add Delete Functionality

Complete the application by displaying all books in a list and adding the ability to delete books.

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function BookCollectionManager() {
  const [books, setBooks] = useState([]);
  const [title, setTitle] = useState("");
  const [author, setAuthor] = useState("");

  // Handle input change for title
  function handleTitleChange(event) {
    setTitle(event.target.value);
  }

  // Handle input change for author
  function handleAuthorChange(event) {
    setAuthor(event.target.value);
  }

  // Add a new book to the list
  function addBook() {
    if (title.trim() !== "" && author.trim() !== "") {
      setBooks((b) => [...b, { title, author }]);
      setTitle("");
      setAuthor(""); // Clear the input fields
    }
  }

  // Delete a book from the list
  function deleteBook(index) {
    const updatedBooks = books.filter((_, i) => i !== index);
    setBooks(updatedBooks);
  }

  return (
    <div className="app-container">
      <h1>Book Collection Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter book title..."
          value={title}
          onChange={handleTitleChange}
          className="input-field"
        />
        <input
          type="text"
          placeholder="Enter author name..."
          value={author}
          onChange={handleAuthorChange}
          className="input-field"
        />
        <button onClick={addBook} className="add-button">
          Add Book
        </button>
      </div>

      <div className="books-section">
        <h2>Your Books ({books.length})</h2>
        {books.length === 0 ? (
          <p className="empty-message">No books yet. Add one to get started!</p>
        ) : (
          <ol className="books-list">
            {books.map((book, index) => (
              <li key={index} className="book-item">
                <div className="book-info">
                  <span className="book-title">{book.title}</span>
                  <span className="book-author">by {book.author}</span>
                </div>
                <button
                  onClick={() => deleteBook(index)}
                  className="delete-button"
                >
                  Delete
                </button>
              </li>
            ))}
          </ol>
        )}
      </div>
    </div>
  );
}

export default BookCollectionManager;
```

#### `src/App.css`

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f5f5f5;
}

.app-container {
  max-width: 600px;
  margin: 40px auto;
  padding: 30px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.app-container h1 {
  color: #2c3e50;
  margin-bottom: 20px;
  font-size: 28px;
}

.input-section {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 30px;
}

.input-field {
  padding: 12px 15px;
  font-size: 16px;
  border: 1px solid #bdc3c7;
  border-radius: 6px;
  transition: border-color 0.3s ease;
}

.input-field:focus {
  outline: none;
  border-color: #3498db;
  box-shadow: 0 0 5px rgba(52, 152, 219, 0.3);
}

.add-button {
  padding: 12px 20px;
  font-size: 16px;
  font-weight: 600;
  color: white;
  background-color: #27ae60;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.1s ease;
}

.add-button:hover {
  background-color: #229954;
}

.add-button:active {
  transform: scale(0.98);
}

.books-section {
  border-top: 2px solid #ecf0f1;
  padding-top: 20px;
}

.books-section h2 {
  color: #2c3e50;
  font-size: 20px;
  margin-bottom: 15px;
}

.empty-message {
  color: #95a5a6;
  font-style: italic;
  text-align: center;
  padding: 20px;
}

.books-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.book-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  background-color: #ecf0f1;
  border-radius: 6px;
  transition: background-color 0.2s ease;
}

.book-item:hover {
  background-color: #d5dbdb;
}

.book-info {
  display: flex;
  flex-direction: column;
  gap: 4px;
  flex: 1;
}

.book-title {
  font-weight: 600;
  color: #2c3e50;
  font-size: 16px;
}

.book-author {
  color: #7f8c8d;
  font-size: 14px;
}

.delete-button {
  padding: 8px 16px;
  font-size: 14px;
  color: white;
  background-color: #e74c3c;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.1s ease;
  margin-left: 10px;
}

.delete-button:hover {
  background-color: #c0392b;
}

.delete-button:active {
  transform: scale(0.98);
}
```

**What you should see**: 
- A complete Book Collection Manager with:
  - Input fields for book title and author
  - An "Add Book" button (green)
  - A list of all books with a counter showing the total number of books
  - A "Delete" button (red) next to each book to remove it from the collection
  - An empty state message when no books are in the collection
  - Smooth hover effects and transitions on buttons
  - Professional styling with a card layout

----

## Part 2

Build a **Shopping Cart** feature with the following functionality:

#### **1. State Management**
Use the `useState` hook to manage:
- The list of cart items  
- Controlled input fields:  
  - `itemName`  
  - `quantity`  
  - `price`

#### **2. Controlled Form Inputs**
All form fields must be controlled components:
- Their values come from state  
- Updating them triggers state updates

#### **3. Add Items**
Implement a function that:
- Creates a new item object  
- Adds it to the cart array  
- Resets the input fields


#### **4. Remove Items**
Each item should have a **Remove** button that:
- Deletes the item from the cart array

#### **5. List Rendering**
Use `.map()` to display all cart items dynamically:
- Show name, quantity, price, and total per item  
- Include update/remove controls


----

## Part 3

### Overview

Throughout the activity, you will switch roles: the driver (who writes code) becomes the navigator (who reviews and guides), and vice versa. Remember to switch roles after each iteration, to ensure both participants contribute to coding and reviewing.

**Commit messages: Recommended format**

Use small commits that describe *what* changed.

Recommended format (Conventional Commits style):

- `feat(routing): add Home and NotFound components`
  - *feat* Short for feature. Used when you add a new feature or new functionality to the codebase.
- `refactor(components): convert Services to use useState`
  - *refactor* used when you change existing code without altering behavior. This improves structure, readability, or organization.
- `chore: install react-router-dom dependency`
  - *chore* used for maintenance tasks that don't change application behavior. Examples: updating dependencies, adding logging, renaming files, config changes.

Rule of thumb:

- One commit = one "idea" that you could explain quickly.
- If a commit breaks the app, it's too big.

### Iteration 0: Project Setup

1. **Decide Initial Roles**:
   - Determine who will start as the driver and who will be the navigator. Remember to switch roles after each major step.

2. **Clone the starter code**:
   - Use the following commands to get started:
     ```bash
     git clone https://github.com/tx00-resources-en/week4-fe-pp-starter week4-fe-pp
     cd week4-fe-pp
     ```
   - **Note**: Remove the `.git` directory to ensure that you start with a fresh Git history for your new repository.
   - Initialize a new Git repository:
     ```bash
     rm -rf .git
     git init
     git add .
     git commit -m "chore: initial project setup from starter template"
     ```

3. **Install Dependencies**:
   - First, install the base project dependencies:
     ```bash
     npm install
     ```
   - Install React Router DOM for client-side routing functionality:
     ```bash
     npm install react-router-dom
     ```
   - Start the development server to verify everything works:
     ```bash
     npm run dev
     ```
   - **Note**: React Router DOM enables navigation between different "pages" in your single-page application without full page refreshes.

### Iteration 1: Basic Routing

Follow the steps below to set up basic routing in your React application.

#### 1. Create `Home.jsx` Component
Create a new file named `Home.jsx` in the `components` folder with the following content:

```jsx
// Home.jsx
function Home() {
  return (
    <div className="temp">
      <h1>This is Home</h1>
      <p>Welcome! Glad you're here.</p>
    </div>
  );
}

export default Home;
```

#### 2. Create `NotFound.jsx` Component
Create another file named `NotFound.jsx` in the `components` folder with the following content:

```jsx
// NotFound.jsx
function NotFound() {
  return (
    <div className="temp">
      <h1>404 - Not Found</h1>
      <p>Oops! The page you are looking for doesn't exist.</p>
    </div>
  );
}

export default NotFound;
```

#### 3. Update `App.jsx` with Basic Routing

  - Open your main `App.jsx` file and update the `App` component to set up the routing. 
  - The final code should look like this:

    ```jsx
    import About from "./components/About";
    import Footer from "./components/Footer";
    import Hero from "./components/Hero";
    import Header from "./components/Header";
    import Services from "./components/Services";
    import Tours from "./components/Tours";
    import Home from "./components/Home";
    import NotFound from "./components/NotFound";
    import "./App.css";
    import { BrowserRouter, Route, Routes } from "react-router-dom";

    function App() {
      return (
        <BrowserRouter>
          <Header />
          <Hero />
          <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/services" element={<Services />} />
            <Route path="/tours" element={<Tours />} />
            <Route path="/about" element={<About />} />
            <Route path="*" element={<NotFound />} />
          </Routes>
          <Footer />
        </BrowserRouter>
      );
    }

    export default App;
    ```

> - The `BrowserRouter` component enables routing functionality for your entire app
> - `Routes` and `Route` components define which component renders for each URL path
> - The `path="*"` route catches any unmatched URLs and shows the NotFound component
> - For advanced routing with nested routes, see Iteration 7

#### 4. Update `PageLink` Component

Open the `PageLink` component file and make the following changes:

- Import the `Link` component from `react-router-dom`. 
- The final code should look like this:

```jsx
import { Link } from "react-router-dom";

const PageLink = ({ link, itemClass }) => {
  return (
    <li>
      <Link to={link.href} className={itemClass}>
        {link.text}
      </Link>
    </li>
  );
};

export default PageLink;
```

#### 5. Update `data.js`
Open the `data.js` file and replace the existing `pageLinks` array (currently using hash links like `#home`) with route paths for React Router navigation:

```jsx
export const pageLinks = [
  { id: 1, href: "/", text: "home" },
  { id: 2, href: "/about", text: "about" },
  { id: 3, href: "/services", text: "services" },
  { id: 4, href: "/tours", text: "tours" },
];
```

**Note**: This changes the navigation from hash-based scrolling to route-based navigation, which works with React Router.

#### 6. Commit Your Changes
Once all changes are made, commit them with a meaningful commit message describing what was done. e.g.
```
feat: implement basic routing with react-router-dom

- Add Home and NotFound components
- Configure BrowserRouter with Routes in App.jsx
- Update PageLink component to use react-router Link
- Modify pageLinks data for route navigation
```

### Iteration 2:

- Refactor the `Services` component so the services array is stored in component state (using `useState`). At the top of the file import useState from React — for example: `import { useState } from 'react';`
- Also keep any other existing imports. Use the state variable (e.g.,`servicesData`) instead of the external services array, and update it with the setter (e.g., `setServicesData`) when removing or restoring services.

```jsx
import { useState } from 'react';
import { services } from "../data";
// Rest of your  imports...

function Services() {
  const [servicesData, setServicesData] = useState(services);

  // Rest of your component logic...

  return (
    // Your JSX structure...
  );
}

export default Services;
```

- **Commit Changes** with a meaningful message. e.g.
```
refactor: convert Services to use local state

- Replace imported data arrays with useState hooks
- Maintain existing functionality with component state
- Prepare components for dynamic data manipulation
```

### Iteration 3:

- Enhance the `Services` component to allow visitors to hide services they are not interested in. Implement a button on each service item for removal, similar to this [`demo`](https://github.com/tx00-web-en/Learning-Material-And-Tasks/tree/week4/material/src/demo3).
- **Commit Changes** with a meaningful message. e.g.
```
feat: add removal functionality to Services

- Implement remove buttons for each service item
- Add click handlers to filter out selected items
- Enhance user interaction with dynamic content removal
```

### Iteration 4:

- Refactor the `Tours` component so the tours array is stored in component state (using `useState`). At the top of the file import useState from React — for example: `import { useState } from 'react';`
- Also keep any other existing imports. Use the state variable (e.g., `toursData`) instead of the external tours array, and update it with the setter (e.g., `setToursData`) when removing or restoring tours.

```jsx
import { useState } from 'react';
import { tours } from "../data";
// Rest of your  imports...

function Tours() {
  const [toursData, setToursData] = useState(tours);

  // Rest of your component logic...

  return (
    // Your JSX structure...
  );
}

export default Tours;
```

- **Commit Changes** with a meaningful message. e.g.
```
refactor: convert Tours to use local state

- Replace imported data arrays with useState hooks
- Maintain existing functionality with component state
- Prepare components for dynamic data manipulation
```


### Iteration 5:

- Enhance the `Tours` component to allow visitors to hide tours they are not interested in. Implement a button on each tour item for removal, similar to this [`demo`](https://github.com/tx00-web-en/Learning-Material-And-Tasks/tree/week4/material/src/demo3).
- **Commit Changes** with a meaningful message. e.g.
```
feat: add removal functionality to Tours component

- Implement remove buttons for each tour item
- Add click handlers to filter out selected items
- Enhance user interaction with dynamic content removal
```

### Iteration 6:

- Write a `Registration` component and update the `Navbar` component to include a link to the new registration form. The `Registration` component should consist of a form with a minimum of five fields (e.g., name, email, password, confirm password, phone number).
- Add a new route `/registration` to your App.jsx routing configuration.
- **Commit Changes** with a meaningful message. e.g.
```
feat: add Registration component with form validation

- Create registration form with 5+ input fields
- Add navigation link and route to registration page
- Include basic form styling and user interaction
```
