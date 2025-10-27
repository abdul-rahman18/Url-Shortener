# 🔗 URL Shortener Backend

## 📘 Overview  
The **URL Shortener** backend is a simple and efficient API that allows users to convert long URLs into short, shareable ones. It also tracks the number of visits for each shortened link.  

If you’ve ever used **Bitly** or noticed the **“Shorten URL”** option in **Google Forms**, this project performs a similar function — built completely using Node.js and Express.

---

## ⚙️ Features  
- ✂️ **Shorten Long URLs:** Converts lengthy URLs into short, unique identifiers.  
- 📈 **Visit Tracking:** Each time a short link is accessed, its visit count increases.  
- 🧠 **MVC Architecture:** Clear separation of logic with Models, Controllers, and Routes.  
- 💾 **Database Support:** Uses MongoDB for storing URLs and their analytics.  
- ⚙️ **Lightweight Middleware:** Uses `express.json()` for parsing incoming JSON requests.  

---

## 🧰 Tech Stack  
- **Backend Framework:** [Express.js](https://expressjs.com/)  
- **Database:** [MongoDB](https://www.mongodb.com/)  
- **ID Generator:** [nanoid](https://www.npmjs.com/package/nanoid)  
- **Architecture:** MVC (Model–View–Controller) pattern  
- **Middleware:** `express.json()`  

---

## 🏗️ Folder Structure  
```
URL-SHORTENER/
├── controllers/
│   └── url.js          # Handles business logic for creating and fetching URLs
│
├── models/
│   └── url.js          # Defines the MongoDB schema for URLs and visit counts
│
├── routes/
│   ├── connect.js      # Establishes MongoDB connection
│   ├── index.js        # Main entry point for all routes
│   └── url.js          # Routes related to URL shortening and redirection
│
├── package.json        # Project dependencies and scripts
├── package-lock.json   # Dependency lock file
├── task.txt            # Optional notes or development tasks
└── README.md           # Project documentation
```

---

## 🚀 How It Works  
1. **POST `/shorten`** – Accepts a long URL and generates a short ID using `nanoid`.  
2. **GET `/:shortId`** – Redirects the user to the original URL and increments its visit counter.  

---

## 🧩 Example Workflow  
**Request:**  
```bash
POST /shorten
Content-Type: application/json

{
  "originalUrl": "https://www.example.com/some/very/long/link"
}
```

**Response:**  
```json
{
  "shortUrl": "http://localhost:5000/abc123",
  "clicks": 0
}
```

**Visiting `http://localhost:5000/abc123`** will:  
- Redirect the user to `https://www.example.com/some/very/long/link`  
- Increase the `clicks` count in MongoDB  

---

## ⚡ Setup Instructions  
1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/url-shortener-backend.git
   cd url-shortener-backend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Create a `.env` file**
   ```bash
   MONGO_URI=your_mongodb_connection_string
   PORT=5000
   ```

4. **Start the server**
   ```bash
   npm start
   ```

5. **Test endpoints** using Postman or cURL.

---

## 💡 Example MongoDB Document  
```json
{
  "_id": "671b92a0f0e2a8d123456789",
  "originalUrl": "https://example.com/some/long/url",
  "shortId": "abc123",
  "clicks": 5
}
```

---

## 🧠 Inspiration  
Inspired by platforms like **Bitly** and **Google Forms**, this project showcases how URL shortening works under the hood — using **Node.js**, **Express**, and **MongoDB**.

---

## 🧾 Note  
This project includes **only the backend** functionality.  
A frontend interface can be built later to make URL shortening and analytics more user-friendly.
