# bhavcopy-frontend
Frontend for [bhavcopy-backend](https://github.com/parthsharma2/bhavcopy-backend).

## Project setup

### Prerequisites
This project requires the following:
- [bhavcopy-backend](https://github.com/parthsharma2/bhavcopy-backend)
- [Node.js](https://nodejs.org/en/download/)

Once you have setup the prerequisites, you can continue with setting up this project.

1. Install node dependencies.
```
npm install
```

2. In the `.env` file update the `VUE_APP_API_URL` variable value to point to your [bhavcopy-backend](https://github.com/parthsharma2/bhavcopy-backend) server.
For e.g. if your `bhavcopy-backend` server is running on `localhost:8000`, set `VUE_APP_API_URL` to `http://localhost:8000/api` (**Please Note:** the trailing `/api`).

3. Setup is now complete. To run the development server execute the following command
```
npm run serve
```

### Build for production
To build for production execute the following command
```
npm run build
```
