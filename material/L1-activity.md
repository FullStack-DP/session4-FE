
# React useState

## Part 1: Book Collection Manager

In this activity, you'll build a **Book Collection Manager** that demonstrates React's `useState` hook. The application will allow users to add and remove books from a collection. We'll build this in 4 iterations, starting with basic setup and progressively adding functionality and styling.

---

### Step 0: Set Up Your Project

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

3. Replace the contents of `src/App.jsx` and `src/App.css` with the code from **Iteration 0** below.

---

### Iteration 0: Basic Setup

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

---

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

---

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

---

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

---

## Final Application Features

Your completed Book Collection Manager includes:
- ✅ **State Management**: Uses `useState` to manage books, title, and author inputs
- ✅ **Dynamic List**: Displays books as they are added
- ✅ **Input Handling**: Two separate handlers for title and author inputs
- ✅ **Add Functionality**: Validates inputs and adds books while clearing the form
- ✅ **Delete Functionality**: Removes books by their index
- ✅ **Responsive Design**: Works on different screen sizes
- ✅ **User Feedback**: Shows empty state, hover effects, and active button states
- ✅ **Professional Styling**: Clean, modern CSS with good typography and colors

---

## Part 2: Add Book Ratings

Now it's time to extend your Book Collection Manager! In this part, you'll modify the application to allow users to rate each book.

### Your Task

Modify your `App.jsx` and `App.css` from Part 1 to:

1. **Add a new input field** for book rating (a number between 1 and 5)
2. **Update the book object** to include the rating property
3. **Create a handler function** to manage the rating input, similar to how you handle title and author
4. **Display the rating** in the book list alongside the title and author
5. **Apply the CSS styles** provided below to style the rating display

### CSS Styling for Ratings

Add these CSS classes to your `src/App.css`:

```css
.rating-container {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: 8px;
}

.rating-label {
  color: #7f8c8d;
  font-size: 14px;
  font-weight: 600;
}

.rating-stars {
  display: inline-flex;
  gap: 4px;
  font-size: 18px;
}

.star {
  color: #f39c12;
  cursor: default;
}

.rating-value {
  color: #2c3e50;
  font-weight: 600;
  font-size: 14px;
  margin-left: 4px;
}
```

Also update your input field styling to include a rating input:

```css
.rating-input {
  padding: 12px 15px;
  font-size: 16px;
  border: 1px solid #bdc3c7;
  border-radius: 6px;
  transition: border-color 0.3s ease;
  /* Allow only numbers from 1-5 */
  width: 100%;
}

.rating-input:focus {
  outline: none;
  border-color: #f39c12;
  box-shadow: 0 0 5px rgba(243, 156, 18, 0.3);
}
```

### Hints

- Use `<input type="number" min="1" max="5">` for the rating input to restrict values
- Remember to clear the rating input when you add a book
- You'll need a new state variable: `rating` and a handler function `handleRatingChange`
- When displaying the rating, consider creating a helper function that shows stars (★) based on the rating value
- Think about validation: should you allow adding a book without a rating?

### What You Should Achieve

When complete, your app should:
- Have an input field for rating (1-5)
- Display ratings in the book list with star icons (★)
- Show the numeric rating value next to the stars
- Clear the rating input when a new book is added
- Have orange/gold colored stars that stand out from the text

---

<details>
<summary><strong>Solution</strong></summary>

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function BookCollectionManager() {
  const [books, setBooks] = useState([]);
  const [title, setTitle] = useState("");
  const [author, setAuthor] = useState("");
  const [rating, setRating] = useState("");

  // Handle input change for title
  function handleTitleChange(event) {
    setTitle(event.target.value);
  }

  // Handle input change for author
  function handleAuthorChange(event) {
    setAuthor(event.target.value);
  }

  // Handle input change for rating
  function handleRatingChange(event) {
    setRating(event.target.value);
  }

  // Add a new book to the list
  function addBook() {
    if (title.trim() !== "" && author.trim() !== "" && rating !== "") {
      setBooks((b) => [...b, { title, author, rating: parseInt(rating) }]);
      setTitle("");
      setAuthor("");
      setRating(""); // Clear the input fields
    }
  }

  // Delete a book from the list
  function deleteBook(index) {
    const updatedBooks = books.filter((_, i) => i !== index);
    setBooks(updatedBooks);
  }

  // Helper function to generate star rating display
  function renderStars(rating) {
    return "★".repeat(rating);
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
        <input
          type="number"
          min="1"
          max="5"
          placeholder="Rating (1-5)..."
          value={rating}
          onChange={handleRatingChange}
          className="rating-input"
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
                  <div className="rating-container">
                    <span className="rating-label">Rating:</span>
                    <span className="rating-stars">
                      <span className="star">{renderStars(book.rating)}</span>
                      <span className="rating-value">{book.rating}/5</span>
                    </span>
                  </div>
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

.rating-input {
  padding: 12px 15px;
  font-size: 16px;
  border: 1px solid #bdc3c7;
  border-radius: 6px;
  transition: border-color 0.3s ease;
  width: 100%;
}

.rating-input:focus {
  outline: none;
  border-color: #f39c12;
  box-shadow: 0 0 5px rgba(243, 156, 18, 0.3);
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

.rating-container {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: 8px;
}

.rating-label {
  color: #7f8c8d;
  font-size: 14px;
  font-weight: 600;
}

.rating-stars {
  display: inline-flex;
  gap: 4px;
  font-size: 18px;
}

.star {
  color: #f39c12;
  cursor: default;
}

.rating-value {
  color: #2c3e50;
  font-weight: 600;
  font-size: 14px;
  margin-left: 4px;
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

### Key Changes Explained:

1. **New State Variable**: `const [rating, setRating] = useState("");` - stores the current rating input
2. **Rating Handler**: `handleRatingChange()` - updates the rating state when user types
3. **Updated addBook()**: Now includes validation for rating and converts it to an integer: `rating: parseInt(rating)`
4. **renderStars() Helper**: Returns star symbols based on the rating number (e.g., rating 4 returns "★★★★")
5. **Rating Display**: Added `.rating-container` div that displays the label, stars, and numeric rating
6. **CSS Classes**: Applied all styling for the rating input and display elements with the gold/orange color (#f39c12)

</details>

---

## Part 3: Contact List Manager

In this activity, you'll build a **Contact List Manager** that demonstrates React's `useState` hook. The application will allow users to add and remove contacts from a list. We'll build this in 4 iterations, starting with basic setup and progressively adding functionality and styling.

---

### Step 0: Set Up Your Project

1. Open your `VS Code` editor in the `week4` directory.
2. Create a new React project and start the development server. For full steps on creating a React project with `Vite`, refer to [these instructions](./vite.md). In brief, run:

   ```bash
   npx create-vite@latest week4-pp-part3 --template react
   cd week4-pp-part3
   npm install
   npm run dev
   ```

   - This will create a new React project named `week4-pp-part3` and start it.
   - **Note**: By default, Vite runs on port `5173`.  
   - When using Vite with React, it's recommended to use the `.jsx` extension for files containing JSX syntax. If a file contains only standard JavaScript, the `.js` extension is fine.

3. Replace the contents of `src/App.jsx` and `src/App.css` with the code from **Iteration 0** below.

---

### Iteration 0: Basic Setup

Create the foundation of your Contact List Manager with basic HTML structure and minimal styling.

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function ContactListManager() {
  const [contacts, setContacts] = useState([]);

  return (
    <div className="app-container">
      <h1>Contact List Manager</h1>
      <p>Welcome! Let's start building your contact list.</p>
    </div>
  );
}

export default ContactListManager;
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

**What you should see**: A centered card with the title "Contact List Manager" and a welcome message.

---

### Iteration 1: Add Input Fields and State Management

Now add state variables for contact name and email, along with input fields for users to enter contact information.

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function ContactListManager() {
  const [contacts, setContacts] = useState([]);
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");

  // Handle input change for name
  function handleNameChange(event) {
    setName(event.target.value);
  }

  // Handle input change for email
  function handleEmailChange(event) {
    setEmail(event.target.value);
  }

  return (
    <div className="app-container">
      <h1>Contact List Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter contact name..."
          value={name}
          onChange={handleNameChange}
          className="input-field"
        />
        <input
          type="email"
          placeholder="Enter email address..."
          value={email}
          onChange={handleEmailChange}
          className="input-field"
        />
      </div>
    </div>
  );
}

export default ContactListManager;
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

**What you should see**: Two input fields where users can type the contact name and email address. The fields should highlight with a blue border when focused.

---

### Iteration 2: Add the "Add Contact" Button

Implement the `addContact` function and button to add contacts to the list.

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function ContactListManager() {
  const [contacts, setContacts] = useState([]);
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");

  // Handle input change for name
  function handleNameChange(event) {
    setName(event.target.value);
  }

  // Handle input change for email
  function handleEmailChange(event) {
    setEmail(event.target.value);
  }

  // Add a new contact to the list
  function addContact() {
    if (name.trim() !== "" && email.trim() !== "") {
      setContacts((c) => [...c, { name, email }]);
      setName("");
      setEmail(""); // Clear the input fields
    }
  }

  return (
    <div className="app-container">
      <h1>Contact List Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter contact name..."
          value={name}
          onChange={handleNameChange}
          className="input-field"
        />
        <input
          type="email"
          placeholder="Enter email address..."
          value={email}
          onChange={handleEmailChange}
          className="input-field"
        />
        <button onClick={addContact} className="add-button">
          Add Contact
        </button>
      </div>
    </div>
  );
}

export default ContactListManager;
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

**What you should see**: A green "Add Contact" button below the input fields. When clicked, it should add the contact to the list (though we haven't displayed the list yet) and clear the input fields.

---

### Iteration 3: Display the Contact List and Add Delete Functionality

Complete the application by displaying all contacts in a list and adding the ability to delete contacts.

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function ContactListManager() {
  const [contacts, setContacts] = useState([]);
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");

  // Handle input change for name
  function handleNameChange(event) {
    setName(event.target.value);
  }

  // Handle input change for email
  function handleEmailChange(event) {
    setEmail(event.target.value);
  }

  // Add a new contact to the list
  function addContact() {
    if (name.trim() !== "" && email.trim() !== "") {
      setContacts((c) => [...c, { name, email }]);
      setName("");
      setEmail(""); // Clear the input fields
    }
  }

  // Delete a contact from the list
  function deleteContact(index) {
    const updatedContacts = contacts.filter((_, i) => i !== index);
    setContacts(updatedContacts);
  }

  return (
    <div className="app-container">
      <h1>Contact List Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter contact name..."
          value={name}
          onChange={handleNameChange}
          className="input-field"
        />
        <input
          type="email"
          placeholder="Enter email address..."
          value={email}
          onChange={handleEmailChange}
          className="input-field"
        />
        <button onClick={addContact} className="add-button">
          Add Contact
        </button>
      </div>

      <div className="contacts-section">
        <h2>Your Contacts ({contacts.length})</h2>
        {contacts.length === 0 ? (
          <p className="empty-message">No contacts yet. Add one to get started!</p>
        ) : (
          <ol className="contacts-list">
            {contacts.map((contact, index) => (
              <li key={index} className="contact-item">
                <div className="contact-info">
                  <span className="contact-name">{contact.name}</span>
                  <span className="contact-email">{contact.email}</span>
                </div>
                <button
                  onClick={() => deleteContact(index)}
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

Export default ContactListManager;
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

.contacts-section {
  border-top: 2px solid #ecf0f1;
  padding-top: 20px;
}

.contacts-section h2 {
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

.contacts-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.contact-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  background-color: #ecf0f1;
  border-radius: 6px;
  transition: background-color 0.2s ease;
}

.contact-item:hover {
  background-color: #d5dbdb;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 4px;
  flex: 1;
}

.contact-name {
  font-weight: 600;
  color: #2c3e50;
  font-size: 16px;
}

.contact-email {
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
- A complete Contact List Manager with:
  - Input fields for contact name and email
  - An "Add Contact" button (green)
  - A list of all contacts with a counter showing the total number of contacts
  - A "Delete" button (red) next to each contact to remove it from the list
  - An empty state message when no contacts are in the list
  - Smooth hover effects and transitions on buttons
  - Professional styling with a card layout

---

## Final Application Features

Your completed Contact List Manager includes:
- ✅ **State Management**: Uses `useState` to manage contacts, name, and email inputs
- ✅ **Dynamic List**: Displays contacts as they are added
- ✅ **Input Handling**: Two separate handlers for name and email inputs
- ✅ **Add Functionality**: Validates inputs and adds contacts while clearing the form
- ✅ **Delete Functionality**: Removes contacts by their index
- ✅ **Responsive Design**: Works on different screen sizes
- ✅ **User Feedback**: Shows empty state, hover effects, and active button states
- ✅ **Professional Styling**: Clean, modern CSS with good typography and colors

---

## Part 4: Add Contact Phone Number

Now it's time to extend your Contact List Manager! In this part, you'll modify the application to allow users to save phone numbers for each contact.

### Your Task

Modify your `App.jsx` and `App.css` from Part 3 to:

1. **Add a new input field** for contact phone number
2. **Update the contact object** to include the phone number property
3. **Create a handler function** to manage the phone number input, similar to how you handle name and email
4. **Display the phone number** in the contact list alongside the name and email
5. **Apply the CSS styles** provided below to style the phone number display

### CSS Styling for Phone Numbers

Add these CSS classes to your `src/App.css`:

```css
.phone-container {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: 8px;
}

.phone-label {
  color: #7f8c8d;
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.phone-number {
  color: #2c3e50;
  font-weight: 600;
  font-size: 14px;
  font-family: 'Courier New', monospace;
}
```

Also update your input field styling to include a phone number input:

```css
.phone-input {
  padding: 12px 15px;
  font-size: 16px;
  border: 1px solid #bdc3c7;
  border-radius: 6px;
  transition: border-color 0.3s ease;
  width: 100%;
}

.phone-input:focus {
  outline: none;
  border-color: #9b59b6;
  box-shadow: 0 0 5px rgba(155, 89, 182, 0.3);
}
```

### Hints

- Use `<input type="tel">` for the phone number input for better mobile experience
- Remember to clear the phone input when you add a contact
- You'll need a new state variable: `phone` and a handler function `handlePhoneChange`
- Phone numbers should be displayed with a label "PHONE:" before the number
- Think about validation: should you allow adding a contact without a phone number?

### What You Should Achieve

When complete, your app should:
- Have an input field for phone number
- Display phone numbers in the contact list with a label
- Use a monospace font for the phone number to make it stand out
- Clear the phone input when a new contact is added
- Have a purple/violet focus color for the phone input field

---

<details>
<summary><strong>Solution</strong></summary>

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function ContactListManager() {
  const [contacts, setContacts] = useState([]);
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");
  const [phone, setPhone] = useState("");

  // Handle input change for name
  function handleNameChange(event) {
    setName(event.target.value);
  }

  // Handle input change for email
  function handleEmailChange(event) {
    setEmail(event.target.value);
  }

  // Handle input change for phone
  function handlePhoneChange(event) {
    setPhone(event.target.value);
  }

  // Add a new contact to the list
  function addContact() {
    if (name.trim() !== "" && email.trim() !== "" && phone.trim() !== "") {
      setContacts((c) => [...c, { name, email, phone }]);
      setName("");
      setEmail("");
      setPhone(""); // Clear the input fields
    }
  }

  // Delete a contact from the list
  function deleteContact(index) {
    const updatedContacts = contacts.filter((_, i) => i !== index);
    setContacts(updatedContacts);
  }

  return (
    <div className="app-container">
      <h1>Contact List Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter contact name..."
          value={name}
          onChange={handleNameChange}
          className="input-field"
        />
        <input
          type="email"
          placeholder="Enter email address..."
          value={email}
          onChange={handleEmailChange}
          className="input-field"
        />
        <input
          type="tel"
          placeholder="Enter phone number..."
          value={phone}
          onChange={handlePhoneChange}
          className="phone-input"
        />
        <button onClick={addContact} className="add-button">
          Add Contact
        </button>
      </div>

      <div className="contacts-section">
        <h2>Your Contacts ({contacts.length})</h2>
        {contacts.length === 0 ? (
          <p className="empty-message">No contacts yet. Add one to get started!</p>
        ) : (
          <ol className="contacts-list">
            {contacts.map((contact, index) => (
              <li key={index} className="contact-item">
                <div className="contact-info">
                  <span className="contact-name">{contact.name}</span>
                  <span className="contact-email">{contact.email}</span>
                  <div className="phone-container">
                    <span className="phone-label">Phone:</span>
                    <span className="phone-number">{contact.phone}</span>
                  </div>
                </div>
                <button
                  onClick={() => deleteContact(index)}
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

Export default ContactListManager;
```

#### `src/App.css`

Add these new CSS classes to your existing `src/App.css`:

```css
.phone-input {
  padding: 12px 15px;
  font-size: 16px;
  border: 1px solid #bdc3c7;
  border-radius: 6px;
  transition: border-color 0.3s ease;
  width: 100%;
}

.phone-input:focus {
  outline: none;
  border-color: #9b59b6;
  box-shadow: 0 0 5px rgba(155, 89, 182, 0.3);
}

.phone-container {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: 8px;
}

.phone-label {
  color: #7f8c8d;
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.phone-number {
  color: #2c3e50;
  font-weight: 600;
  font-size: 14px;
  font-family: 'Courier New', monospace;
}
```

### Key Changes Explained:

1. **New State Variable**: `const [phone, setPhone] = useState("");` - stores the current phone input
2. **Phone Handler**: `handlePhoneChange()` - updates the phone state when user types
3. **Updated addContact()**: Now includes validation for phone and adds it to the contact object
4. **Phone Display**: Added `.phone-container` div that displays the phone label and number with monospace font
5. **CSS Classes**: Applied styling for the phone input with purple focus state and the phone display with uppercase label

</details>


-----


---

## Part 5: Recipe Manager

In this activity, you'll build a **Recipe Manager** that demonstrates React's useState hook. The application will allow users to add and remove recipes from a collection. We'll build this in 4 iterations, starting with basic setup and progressively adding functionality and styling.

---

### Step 0: Set Up Your Project

1. Open your VS Code editor in the week4 directory.
2. Create a new React project and start the development server. For full steps on creating a React project with Vite, refer to [these instructions](./vite.md). In brief, run:

   ```ash
   npx create-vite@latest week4-pp-part5 --template react
   cd week4-pp-part5
   npm install
   npm run dev
   ```

   - This will create a new React project named week4-pp-part5 and start it.
   - **Note**: By default, Vite runs on port 5173.  
   - When using Vite with React, it's recommended to use the .jsx extension for files containing JSX syntax. If a file contains only standard JavaScript, the .js extension is fine.

3. Replace the contents of src/App.jsx and src/App.css with the code from **Iteration 0** below.

---

### Iteration 0: Basic Setup

Create the foundation of your Recipe Manager with basic HTML structure and minimal styling.

#### \src/App.jsx\

```jsx
import React, { useState } from "react";
import "./App.css";

function RecipeManager() {
  const [recipes, setRecipes] = useState([]);

  return (
    <div className="app-container">
      <h1>Recipe Manager</h1>
      <p>Welcome! Let's start building your recipe collection.</p>
    </div>
  );
}

export default RecipeManager;
```

#### \src/App.css\

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

**What you should see**: A centered card with the title "Recipe Manager" and a welcome message.

---

### Iteration 1: Add Input Fields and State Management

Now add state variables for recipe name and ingredients, along with input fields for users to enter recipe information.

#### \src/App.jsx\

```jsx
import React, { useState } from "react";
import "./App.css";

function RecipeManager() {
  const [recipes, setRecipes] = useState([]);
  const [name, setName] = useState("");
  const [ingredients, setIngredients] = useState("");

  // Handle input change for name
  function handleNameChange(event) {
    setName(event.target.value);
  }

  // Handle input change for ingredients
  function handleIngredientsChange(event) {
    setIngredients(event.target.value);
  }

  return (
    <div className="app-container">
      <h1>Recipe Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter recipe name..."
          value={name}
          onChange={handleNameChange}
          className="input-field"
        />
        <textarea
          placeholder="Enter ingredients (one per line)..."
          value={ingredients}
          onChange={handleIngredientsChange}
          className="input-field"
          rows="4"
        ></textarea>
      </div>
    </div>
  );
}

export default RecipeManager;
```

#### \src/App.css\

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
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.input-field:focus {
  outline: none;
  border-color: #3498db;
  box-shadow: 0 0 5px rgba(52, 152, 219, 0.3);
}
```

**What you should see**: An input field for recipe name and a textarea for ingredients. The fields should highlight with a blue border when focused.

This represents a good stopping point for part 1 of the recipe manager. Please continue this pattern with Iteration 2 and 3, along with Part 6 for the cooking time feature when ready.

---

### Iteration 2: Add the "Add Recipe" Button

Implement the \ddRecipe\ function and button to add recipes to the collection.

#### \src/App.jsx\

```jsx
import React, { useState } from "react";
import "./App.css";

function RecipeManager() {
  const [recipes, setRecipes] = useState([]);
  const [name, setName] = useState("");
  const [ingredients, setIngredients] = useState("");

  // Handle input change for name
  function handleNameChange(event) {
    setName(event.target.value);
  }

  // Handle input change for ingredients
  function handleIngredientsChange(event) {
    setIngredients(event.target.value);
  }

  // Add a new recipe to the list
  function addRecipe() {
    if (name.trim() !== "" && ingredients.trim() !== "") {
      setRecipes((r) => [...r, { name, ingredients }]);
      setName("");
      setIngredients(""); // Clear the input fields
    }
  }

  return (
    <div className="app-container">
      <h1>Recipe Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter recipe name..."
          value={name}
          onChange={handleNameChange}
          className="input-field"
        />
        <textarea
          placeholder="Enter ingredients (one per line)..."
          value={ingredients}
          onChange={handleIngredientsChange}
          className="input-field"
          rows="4"
        ></textarea>
        <button onClick={addRecipe} className="add-button">
          Add Recipe
        </button>
      </div>
    </div>
  );
}

export default RecipeManager;
```

This completes Iteration 2. The button styling is included in the CSS below:

```css
.add-button {
  padding: 12px 20px;
  font-size: 16px;
  font-weight: 600;
  color: white;
  background-color: #e67e22;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.1s ease;
}

.add-button:hover {
  background-color: #d35400;
}

.add-button:active {
  transform: scale(0.98);
}
```

---

### Iteration 3: Display the Recipe List and Add Delete Functionality

Complete the application by displaying all recipes in a list and adding the ability to delete recipes.

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function RecipeManager() {
  const [recipes, setRecipes] = useState([]);
  const [name, setName] = useState("");
  const [ingredients, setIngredients] = useState("");

  function handleNameChange(event) {
    setName(event.target.value);
  }

  function handleIngredientsChange(event) {
    setIngredients(event.target.value);
  }

  function addRecipe() {
    if (name.trim() !== "" && ingredients.trim() !== "") {
      setRecipes((r) => [...r, { name, ingredients }]);
      setName("");
      setIngredients("");
    }
  }

  function deleteRecipe(index) {
    const updatedRecipes = recipes.filter((_, i) => i !== index);
    setRecipes(updatedRecipes);
  }

  return (
    <div className="app-container">
      <h1>Recipe Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter recipe name..."
          value={name}
          onChange={handleNameChange}
          className="input-field"
        />
        <textarea
          placeholder="Enter ingredients (one per line)..."
          value={ingredients}
          onChange={handleIngredientsChange}
          className="input-field"
          rows="4"
        ></textarea>
        <button onClick={addRecipe} className="add-button">
          Add Recipe
        </button>
      </div>

      <div className="recipes-section">
        <h2>Your Recipes ({recipes.length})</h2>
        {recipes.length === 0 ? (
          <p className="empty-message">No recipes yet. Add your first recipe above!</p>
        ) : (
          <ol className="recipes-list">
            {recipes.map((recipe, index) => (
              <li key={index} className="recipe-item">
                <div className="recipe-name">{recipe.name}</div>
                <div className="recipe-ingredients">
                  {recipe.ingredients.replace(/\n/g, ", ")}
                </div>
                <button
                  onClick={() => deleteRecipe(index)}
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

export default RecipeManager;
```

#### `src/App.css` (Add these additional styles)

```css
.recipes-section {
  margin-top: 30px;
  padding-top: 20px;
  border-top: 2px solid #ecf0f1;
}

.recipes-section h2 {
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

.recipes-list {
  list-style-position: inside;
  padding-left: 0;
}

.recipe-item {
  background-color: #f9f9f9;
  padding: 15px;
  margin-bottom: 12px;
  border-left: 4px solid #e67e22;
  border-radius: 4px;
}

.recipe-name {
  font-weight: 600;
  color: #2c3e50;
  font-size: 18px;
  margin-bottom: 8px;
}

.recipe-ingredients {
  color: #7f8c8d;
  font-size: 14px;
  margin-bottom: 10px;
  line-height: 1.5;
}

.delete-button {
  padding: 8px 12px;
  font-size: 14px;
  color: white;
  background-color: #e74c3c;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.delete-button:hover {
  background-color: #c0392b;
}
```

**What you should see**: A list of recipes with their names and ingredients, plus a delete button for each recipe.

---

## Part 6: Add Cooking Time to Recipes

Now extend your Recipe Manager to include cooking time! In this part, you'll modify the application to allow users to save cooking time for each recipe.

### Your Task

Modify your `App.jsx` and `App.css` from Part 5 to:

1. **Add a new input field** for cooking time (in minutes)
2. **Update the recipe object** to include the cooking time property
3. **Create a handler function** to manage the cooking time input
4. **Display the cooking time** in the recipe list
5. **Apply the CSS styles** provided below

### CSS Styling for Cooking Time

```css
.time-input {
  padding: 12px 15px;
  font-size: 16px;
  border: 1px solid #bdc3c7;
  border-radius: 6px;
  transition: border-color 0.3s ease;
}

.time-input:focus {
  outline: none;
  border-color: #e67e22;
  box-shadow: 0 0 5px rgba(230, 126, 34, 0.3);
}

.time-container {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: 8px;
}

.time-label {
  color: #7f8c8d;
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.time-value {
  color: #2c3e50;
  font-weight: 600;
  font-size: 14px;
  background-color: #fef5e7;
  padding: 4px 8px;
  border-radius: 4px;
  font-family: 'Courier New', monospace;
}
```

### Hints

- Use `<input type="number">` for the cooking time input
- Add \handleCookingTimeChange()\ function
- Clear the cooking time when adding a recipe
- Display time as "X minutes"

### What You Should Achieve

- Input field for cooking time (number input)
- Display cooking time with label and light yellow background
- Clear cooking time input when recipe is added
- Orange focus color for the time input field

---

<details>
<summary><strong>Solution</strong></summary>

Here's the complete solution with cooking time integration:

#### `src/App.jsx`

```jsx
import React, { useState } from "react";
import "./App.css";

function RecipeManager() {
  const [recipes, setRecipes] = useState([]);
  const [name, setName] = useState("");
  const [ingredients, setIngredients] = useState("");
  const [cookingTime, setCookingTime] = useState("");

  function handleNameChange(event) {
    setName(event.target.value);
  }

  function handleIngredientsChange(event) {
    setIngredients(event.target.value);
  }

  function handleCookingTimeChange(event) {
    setCookingTime(event.target.value);
  }

  function addRecipe() {
    if (name.trim() !== "" && ingredients.trim() !== "" && cookingTime.trim() !== "") {
      setRecipes((r) => [...r, { name, ingredients, cookingTime: parseInt(cookingTime) }]);
      setName("");
      setIngredients("");
      setCookingTime("");
    }
  }

  function deleteRecipe(index) {
    const updatedRecipes = recipes.filter((_, i) => i !== index);
    setRecipes(updatedRecipes);
  }

  return (
    <div className="app-container">
      <h1>Recipe Manager</h1>
      
      <div className="input-section">
        <input
          type="text"
          placeholder="Enter recipe name..."
          value={name}
          onChange={handleNameChange}
          className="input-field"
        />
        <textarea
          placeholder="Enter ingredients (one per line)..."
          value={ingredients}
          onChange={handleIngredientsChange}
          className="input-field"
          rows="4"
        ></textarea>
        <input
          type="number"
          placeholder="Enter cooking time (minutes)..."
          value={cookingTime}
          onChange={handleCookingTimeChange}
          className="time-input"
          min="1"
        />
        <button onClick={addRecipe} className="add-button">
          Add Recipe
        </button>
      </div>

      <div className="recipes-section">
        <h2>Your Recipes ({recipes.length})</h2>
        {recipes.length === 0 ? (
          <p className="empty-message">No recipes yet. Add your first recipe above!</p>
        ) : (
          <ol className="recipes-list">
            {recipes.map((recipe, index) => (
              <li key={index} className="recipe-item">
                <div className="recipe-name">{recipe.name}</div>
                <div className="recipe-ingredients">
                  {recipe.ingredients.replace(/\n/g, ", ")}
                </div>
                <div className="time-container">
                  <span className="time-label">Cooking Time:</span>
                  <span className="time-value">{recipe.cookingTime} minutes</span>
                </div>
                <button
                  onClick={() => deleteRecipe(index)}
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

export default RecipeManager;
```

#### `src/App.css` (Complete styles including Part 6 additions)

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
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.input-field:focus {
  outline: none;
  border-color: #e67e22;
  box-shadow: 0 0 5px rgba(230, 126, 34, 0.3);
}

.time-input {
  padding: 12px 15px;
  font-size: 16px;
  border: 1px solid #bdc3c7;
  border-radius: 6px;
  transition: border-color 0.3s ease;
}

.time-input:focus {
  outline: none;
  border-color: #e67e22;
  box-shadow: 0 0 5px rgba(230, 126, 34, 0.3);
}

.add-button {
  padding: 12px 20px;
  font-size: 16px;
  font-weight: 600;
  color: white;
  background-color: #e67e22;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.1s ease;
}

.add-button:hover {
  background-color: #d35400;
}

.add-button:active {
  transform: scale(0.98);
}

.recipes-section {
  margin-top: 30px;
  padding-top: 20px;
  border-top: 2px solid #ecf0f1;
}

.recipes-section h2 {
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

.recipes-list {
  list-style-position: inside;
  padding-left: 0;
}

.recipe-item {
  background-color: #f9f9f9;
  padding: 15px;
  margin-bottom: 12px;
  border-left: 4px solid #e67e22;
  border-radius: 4px;
}

.recipe-name {
  font-weight: 600;
  color: #2c3e50;
  font-size: 18px;
  margin-bottom: 8px;
}

.recipe-ingredients {
  color: #7f8c8d;
  font-size: 14px;
  margin-bottom: 10px;
  line-height: 1.5;
}

.time-container {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 10px;
}

.time-label {
  color: #7f8c8d;
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.time-value {
  color: #2c3e50;
  font-weight: 600;
  font-size: 14px;
  background-color: #fef5e7;
  padding: 4px 8px;
  border-radius: 4px;
  font-family: 'Courier New', monospace;
}

.delete-button {
  padding: 8px 12px;
  font-size: 14px;
  color: white;
  background-color: #e74c3c;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.delete-button:hover {
  background-color: #c0392b;
}
```

### Key Changes Explained

1. **New State Variable**: `cookingTime` tracks the input value for cooking time
2. **New Handler**: `handleCookingTimeChange()` updates the cooking time state
3. **Updated addRecipe()**: Now validates that cooking time is not empty, converts it to an integer, and includes it in the recipe object
4. **Updated Display**: Each recipe now shows cooking time with a label and special styling (light yellow background)
5. **Clear on Add**: When a recipe is added, `cookingTime` is cleared with `setCookingTime("")`

</details>

-----


----

## Part 7

Develop a Shopping Cart where users can add, update quantities, and remove items:
- **State Management**: Use the `useState` hook to manage cart items and input fields (`item name`, `quantity`, `price`).
- **Controlled Forms**: Use controlled components for inputs.
- **List Rendering**: Display items dynamically with the `.map()` function.
- **Functions**: Implement functions to add items, update quantities, and remove items.

**Example**

```jsx
<RecipeShoppingCartManager />
```