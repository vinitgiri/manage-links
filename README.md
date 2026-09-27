# 🔗 Link Manager

A simple, modern, and responsive **Link Manager Web Application** built with **HTML, CSS, and Vanilla JavaScript**.

Link Manager allows you to save important URLs, automatically generate useful website information, search saved links, edit URLs, and delete links. All saved links are stored locally in your browser using **localStorage**, so no database or account is required.

## ✨ Features

* 🔗 **Save Links** — Add and store your favorite URLs.
* 🔍 **Search Links** — Search by title, URL, domain, or description.
* 🌐 **Automatic Website Metadata** — Attempts to fetch:

  * Website title
  * Description
  * Favicon / website icon
  * Domain name
* 💾 **Local Storage** — Links remain saved after refreshing or reopening the browser.
* ✏️ **Edit Links** — Update the saved URL and automatically regenerate its metadata.
* 🗑️ **Delete Links** — Remove unwanted links easily.
* 🚀 **Open Links** — Open saved websites directly in a new browser tab.
* 📱 **Responsive Design** — Works on desktop, tablet, and mobile screens.
* 🎨 **Modern Dark UI** — Clean card-based interface with a responsive layout.
* 🛡️ **URL Validation** — Only valid `http://` and `https://` URLs are accepted.
* 🚫 **Duplicate Prevention** — Prevents saving the same URL multiple times.

## 🛠️ Technologies Used

* **HTML5** — Application structure
* **CSS3** — Styling, responsive layout, animations and dark UI
* **JavaScript (ES6+)** — Application logic and DOM manipulation
* **Browser LocalStorage** — Persistent client-side data storage
* **Jina AI Proxy** — Used as a fallback for fetching webpage metadata
* **JSONLink API** — Used for retrieving website metadata
* **Google Favicon Service** — Used as a favicon fallback

## 📂 Project Structure

```text
manage-links/
│
├── index.html
├── style.css
├── package.json
│
├── js/
│   ├── api.js
│   ├── main.js
│   ├── storage.js
│   └── ui.js
│
└── .vscode/
```

### File Description

| File            | Description                                                       |
| --------------- | ----------------------------------------------------------------- |
| `index.html`    | Main application layout and interface                             |
| `style.css`     | Complete responsive dark-theme styling                            |
| `js/main.js`    | Application initialization, validation, search and event handling |
| `js/api.js`     | URL handling and website metadata fetching                        |
| `js/storage.js` | LocalStorage operations and ID generation                         |
| `js/ui.js`      | Link-card rendering and edit/delete/open controls                 |
| `package.json`  | Project metadata and start script                                 |

## ⚙️ How It Works

### 1. Add a Link

Enter a valid URL beginning with:

```text
https://
```

or

```text
http://
```

The application validates the URL before saving it.

### 2. Fetch Website Information

When a link is added, the application attempts to retrieve website metadata.

The metadata process uses the following approach:

```text
User enters URL
      ↓
URL Validation
      ↓
JSONLink Metadata API
      ↓
If unavailable → Jina AI Proxy
      ↓
If metadata still unavailable
      ↓
Generate fallback information
      ↓
Save link
```

### 3. Store the Link

Each saved link contains information such as:

```javascript
{
  id: "...",
  url: "https://example.com",
  title: "Example Link",
  description: "Website description",
  domain: "example.com",
  favicon: "...",
  createdAt: "..."
}
```

The data is stored in the browser's LocalStorage using:

```text
linkManager.links.v1
```

### 4. Search

The search box dynamically filters saved links using:

* Title
* URL
* Domain
* Description

### 5. Edit

The **Edit** button allows you to change the saved URL.

After changing the URL, the application regenerates:

* Domain
* Favicon
* Title
* Description

### 6. Delete

The **Delete** button removes the selected link from LocalStorage after confirmation.

## 🚀 Getting Started

### Prerequisites

No framework, database, or build tool is required.

You only need a modern web browser such as:

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari

### Run Locally

Clone the repository:

```bash
git clone https://github.com/vinitgiri/manage-links.git
```

Navigate to the project:

```bash
cd manage-links
```

Then open:

```text
index.html
```

directly in your browser.

### Using VS Code

You can also open the project in VS Code:

```bash
code .
```

Then open `index.html`.

For the best development experience, you can use the **Live Server** extension in VS Code.

## 📦 npm

This project does not require external npm dependencies.

The included `package.json` provides a simple start script:

```bash
npm start
```

The command reminds you to open `index.html` in your browser.

## 💾 Data Storage

This application is completely client-side.

Saved links are stored using:

```javascript
localStorage
```

Storage key:

```text
linkManager.links.v1
```

This means:

* ✅ No login required
* ✅ No backend required
* ✅ No database required
* ✅ Data persists after page refresh
* ✅ Data is stored locally in the user's browser

Clearing browser site data or LocalStorage will remove the saved links.

## 🌐 Metadata & External Services

The application uses external services when trying to retrieve website metadata.

### JSONLink

Used as the primary metadata extraction service.

```text
https://jsonlink.io/
```

### Jina AI Proxy

Used as a fallback to retrieve webpage content when direct metadata fetching is unavailable.

```text
https://r.jina.ai/
```

### Google Favicon Service

Used as a fallback favicon provider.

```text
https://www.google.com/s2/favicons
```

Because these services are external, metadata retrieval may occasionally fail due to service availability, CORS restrictions, rate limits, or website restrictions.

The application is designed to **save the URL even when metadata cannot be retrieved**.

## 🔐 Privacy

Link Manager does not require an account or send your complete saved-link collection to a personal backend.

Your saved links are stored in your browser's LocalStorage.

However, when adding a URL, the application may send that URL to external metadata services to retrieve website information.

## 🎯 Use Cases

Link Manager can be useful for:

* 📚 Students collecting study resources
* 💻 Developers saving documentation
* 📰 Saving articles and blogs
* 🎓 Managing learning resources
* 🔖 Bookmarking useful websites
* 🧑‍💻 Managing project references
* 🔗 Keeping frequently used URLs organized

## 🔮 Future Improvements

Possible future enhancements include:

* 🔐 User authentication
* ☁️ Cloud synchronization
* 📁 Link categories and folders
* ⭐ Favorites
* 🏷️ Tags
* 📌 Pinned links
* 📊 Link analytics
* 📤 Import / Export links
* 🌙 Theme customization
* 🔄 Multi-device synchronization
* 🗄️ Backend database support

## 🤝 Contributing

Contributions are welcome.

1. Fork the repository
2. Create a new branch

```bash
git checkout -b feature/new-feature
```

3. Make your changes
4. Commit your changes

```bash
git commit -m "Add new feature"
```

5. Push the branch

bash
git push origin feature/new-feature
```

6. Open a Pull Request

## 📜 License

This project does not currently specify a license.

If you plan to allow reuse, modification, or redistribution, consider adding an appropriate open-source license such as the MIT License.

## 👨‍💻 Author

**Vinit Giri**

GitHub: [@vinitgiri](https://github.com/vinitgiri)

--

⭐ If you find this project useful, consider giving the repository a star!

**Repository:**
https://github.com/vinitgiri/manage-links

