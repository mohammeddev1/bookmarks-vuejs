# Bookmark Manager

A modern, user-friendly bookmark management application built with Vue 3. This application allows you to save, organize, search, edit, and delete your favorite website bookmarks with a clean and intuitive interface.

## 🌐 Live Demo

Visit the live application: [GitHub Pages](https://mohammeddev1.github.io/bookmarks-vuejs/)

**Repository**: [bookmarks-vuejs](https://github.com/mohammeddev1/bookmarks-vuejs)

## Features

- ✅ **Add Bookmarks**: Easily add new bookmarks with a title and URL
- ✅ **Edit Bookmarks**: Update existing bookmark information
- ✅ **Delete Bookmarks**: Remove bookmarks with confirmation dialogs
- ✅ **Search Functionality**: Quickly find bookmarks by searching through titles
- ✅ **Local Storage**: All bookmarks are saved locally in your browser
- ✅ **Form Validation**: Input validation ensures data integrity
- ✅ **Beautiful UI**: Modern, responsive design built with TailwindCSS
- ✅ **Sweet Alerts**: User-friendly notifications for all actions

## Tech Stack

- **Vue 3** - Progressive JavaScript framework
- **Vite** - Next generation frontend tooling
- **TailwindCSS** - Utility-first CSS framework
- **SweetAlert2** - Beautiful, responsive, customizable replacement for JavaScript's popup boxes
- **LocalStorage** - Browser-based data persistence

## Project Structure

```
src/
├── components/
│   ├── layouts/
│   │   ├── BookmarkCard.vue      # Individual bookmark card component
│   │   ├── BookmarkForm.vue      # Form for adding new bookmarks
│   │   ├── EditeBookmark.vue     # Form for editing existing bookmarks
│   │   ├── bookmarkList.vue      # List container for bookmarks
│   │   └── NavBar.vue            # Navigation bar component
│   └── ui/
│       ├── BaseButton.vue        # Reusable button component
├── views/
│   └── HomeView.vue              # Main application view
└── styles/
    └── main.css                  # Global styles
```

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Recommended Browser Setup

- Chromium-based browsers (Chrome, Edge, Brave, etc.):
  - [Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
  - [Turn on Custom Object Formatter in Chrome DevTools](http://bit.ly/object-formatters)
- Firefox:
  - [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
  - [Turn on Custom Object Formatter in Firefox DevTools](https://fxdx.dev/firefox-devtools-custom-object-formatters/)

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
