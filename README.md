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
    <UserSignUp />
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

## API Integration for User Sign-Up

The **User Sign-Up** feature includes an API call to register user data. This is implemented in the `UserSignUp.vue` component using `axios`.

### API Endpoint

- **URL**: `http://localhost:3000/user`
- **Method**: `POST`
- **Description**: This endpoint is used to send user registration data to the server.

### Request Payload

The following data is sent in the request body:

```json
{
  "name": "string",
  "email": "string",
  "password": "string"
}
```

### Response

- **Success**: The server responds with the registered user data.
- **Failure**: The server returns an error message if the request fails.

### Implementation in `UserSignUp.vue`

#### Code Snippet

```javascript
methods: {
  async handleSubmit() {
    try {
      // Send user data to the API
      const user = await axios.post("http://localhost:3000/user", this.user);

      // Store user info in localStorage
      localStorage.setItem("user-info", JSON.stringify(user.data));

      // Reset the form fields
      this.user = {
        name: "",
        email: "",
        password: "",
      };

      // Redirect to the home page
      this.$router.push({ name: "home" });
    } catch (error) {
      console.error("Error during sign-up:", error);
    }
  },
}
```

### How It Works

1. **Form Submission**:

   - When the user submits the form, the `handleSubmit` method is triggered.
   - The form data (`name`, `email`, `password`) is bound to the `user` object using `v-model`.

2. **API Call**:

   - The `axios.post` method sends the `user` object to the API endpoint (`http://localhost:3000/user`).

3. **Local Storage**:

   - The response from the API is stored in the browser's `localStorage` under the key `user-info`.

4. **Form Reset**:

   - After a successful API call, the form fields are cleared by resetting the `user` object.

5. **Redirection**:
   - The user is redirected to the home page using `this.$router.push({ name: "home" })`.

### Notes

- Ensure the API server is running at `http://localhost:3000`.
- The `axios` library must be installed in the project. If not, install it using:
  ```sh
  npm install axios
  ```
- Handle errors gracefully to improve the user experience.

### Example API Response

#### Success Response

```json
{
  "id": 1,
  "name": "John Doe",
  "email": "johndoe@example.com",
  "password": "hashed_password"
}
```

#### Error Response

```json
{
  "error": "Email already exists"
}
```

This documentation explains how the API call is integrated into the `UserSignUp.vue` component and how it works within the application.

### Notes

- Ensure the `UserSignUp.vue` component is correctly implemented and exported in the `src/components` directory.
- The route `/usersignup` must be accessible in the application for this feature to work.
