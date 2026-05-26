React Toast Notifications and Profile Features
This project enhancement includes:

Toast notifications using react-hot-toast

Displaying articles in responsive grid cards from the UserProfile component

Author-related functionality in the AuthorProfile component

These features improve user experience, notifications, and responsive UI design in React applications.

Using Toast in React App
Toast notifications are used to display success, error, or warning messages in a clean and interactive way.

Step 1: Install react-hot-toast
Run the following command in the project terminal:

Bash

npm install react-hot-toast
Step 2: Add Toaster Component in Root
Import and place the Toaster component inside App.jsx.

App.jsx
JavaScript

import { Toaster } from "react-hot-toast";

function App() {
  return (
    <div>
      <Toaster position="top-center" reverseOrder={false} />
    </div>
  );
}

export default App;
Step 3: Use Toast Messages
Import toast wherever notifications are required.

Example
JavaScript

import toast from "react-hot-toast";

if (resObj.status === 201) {
  toast.success("Account created successfully");
  navigate("/login");
}
Toast Types
Success Message
JavaScript

toast.success("Login successful");
Error Message
JavaScript

toast.error("Invalid credentials");
Loading Message
JavaScript

toast.loading("Please wait...");
UserProfile Component
Read Articles of All Authors
The UserProfile component fetches and displays articles created by different authors.

Display Articles in Grid Layout
The articles should be displayed using responsive CSS Grid.

Grid Requirements
Screen Size	Cards Per Row
Extra Small	1 Card
Small	2 Cards
Medium	3 Cards
Large and Above	4 Cards

Example JSX
JavaScript

<div className="articles-grid">
  {articles.map((article) => (
    <div className="article-card" key={article._id}>
      <h2>{article.title}</h2>
      <p>{article.content}</p>
      <p>{article.author}</p>
    </div>
  ))}
</div>
Example CSS
CSS

.articles-grid {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(1, 1fr);
}

@media (min-width: 576px) {
  .articles-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 768px) {
  .articles-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (min-width: 992px) {
  .articles-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

.article-card {
  border: 1px solid #ddd;
  padding: 16px;
  border-radius: 10px;
}
AuthorProfile Component
The AuthorProfile component is used for managing author-related operations such as:

Creating articles

Updating articles

Deleting articles

Viewing authored posts

Example Features
Add new article

Edit article

Delete article

View all authored articles

Manage article content

Example Create Article Form
JavaScript

<form>
  <input type="text" placeholder="Article Title" />
  
  <textarea placeholder="Write article content"></textarea>
  
  <button type="submit">
    Add Article
  </button>
</form>
Technologies Used
React JS

Vite

CSS

react-hot-toast

JavaScript

Learning Outcomes
By implementing these features, you will learn:

Using toast notifications in React

Improving user experience with alerts

Responsive Grid layouts

Rendering dynamic data

React component structuring

Managing API data

Responsive UI design

Future Enhancements
Add dark mode

Add article search

Add pagination

Add article categories

Add edit and delete confirmations

Add loading spinners
