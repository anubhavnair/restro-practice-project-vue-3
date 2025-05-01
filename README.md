# Restro-Prac-Project
        

This project is a practice application while learning **Vue 3** and built with **Vue 3** and **Vite**. It serves as a starting point for developing modern web applications.

## Developer
- **Anubhav Nayar**
## Recommended IDE Setup

- [VSCode](https://code.visualstudio.com/)


## Project Setup

To get started with the project, follow these steps:

### Install Dependencies

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

### Lint and Fix Files

```sh
npm run lint
```

## Customize Configuration

For more details, see the [Vite Configuration Reference](https://vite.dev/config/).

## Features

- Vue 3 Options API
- Vite for fast builds and hot module replacement
- ESLint for code quality
- Tailwind CSS (if applicable)

## Folder Structure

```plaintext
src/
├── assets/         # Static assets
├── components/     # Vue components
├── views/          # View components (pages)
├── router/         # Vue Router setup
├── store/          # Vuex/Pinia store (if applicable)
├── App.vue         # Root component
├── main.js         # Entry point
```

## License

This project is licensed under the MIT License.

## User Sign-Up Feature

The **User Sign-Up** feature allows users to register for the application. It consists of a dedicated view and a reusable component.

### Files Involved

1. **View**: `UserSignUpView.vue`
   - Filepath: `src/views/UserSignUpView.vue`
   - This is the main view for the user sign-up page. It imports and uses the `UserSignUp` component.

2. **Component**: `UserSignUp.vue`
   - Filepath: `src/components/UserSignUp.vue`
   - This component contains the form and logic for user registration.

3. **Router Configuration**: `index.js`
   - Filepath: `src/router/index.js`
   - The route for the user sign-up page is defined as follows:
     ```javascript
     {
       path: '/usersignup',
       name: 'signup',
       component: UserSignUpView,
     }
     ```

### How It Works

1. **Route Setup**:
   - The `/usersignup` route is mapped to the `UserSignUpView` component in the router configuration (`src/router/index.js`).

2. **View Structure**:
   - The `UserSignUpView.vue` file imports the `UserSignUp` component and renders it within a `<div>` container.

3. **Component Integration**:
   - The `UserSignUp` component is registered locally in the `UserSignUpView` file and is used to display the sign-up form.

### Usage

- Navigate to `/usersignup` in the browser to access the user sign-up page.
- The `UserSignUp` component will handle the form logic and user input.

### Example Code Snippets

#### Router Configuration
```javascript
{
  path: '/usersignup',
  name: 'signup',
  component: UserSignUpView,
}
```

#### View File (`UserSignUpView.vue`)
```vue
<template>
  <div class="user-signup-view">
    <UserSignUp/>
  </div>
</template>

<script>
import UserSignUp from "@/components/UserSignUp.vue";
export default {
  name: "UserSignUpView",
  components: {
    UserSignUp,
  },
};
</script>
```

### Notes

- Ensure the `UserSignUp.vue` component is correctly implemented and exported in the `src/components` directory.
- The route `/usersignup` must be accessible in the application for this feature to work.