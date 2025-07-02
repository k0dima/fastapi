Run server:

- fastapi dev main.py
- uvicorn main:app --reload
- python3 main.py

Run server:

- fastapi dev main.py
- uvicorn main:app --reload
- python3 main.py

## Deployment

This section describes how to deploy your FastAPI application as a Docker image to free hosting services.

### 1. Render

Render offers a generous free tier for web services. Follow these steps to deploy your application:

1.  **Sign up/Log in:** Go to [Render](https://render.com/) and sign up or log in to your account.
2.  **New Web Service:** From your dashboard, click "New" -> "Web Service".
3.  **Connect Git Repository:** Connect your GitHub or GitLab repository where your `module09` code resides. Make sure the `Dockerfile` and `requirements.txt` are in the root of your repository (or adjust the build context accordingly).
4.  **Configure Service:**
    - **Root Directory:** If your `module09` is not at the root of your repository, set this to `module09/`.
    - **Runtime:** Choose `Docker`.
    - **Build Command:** Leave empty as Docker handles the build process.
    - **Start Command:** `uvicorn main:app --host 0.0.0.0 --port $PORT` (Render automatically injects the `PORT` environment variable).
    - **Instance Type:** Select `Free`.
5.  **Create Web Service:** Click "Create Web Service". Render will automatically build your Docker image and deploy your application.

### 2. Heroku

Heroku also provides a free tier, but it requires a credit card for verification. Here's how to deploy:

1.  **Install Heroku CLI:** If you haven't already, install the Heroku CLI from [Heroku Dev Center](https://devcenter.heroku.com/articles/heroku-cli).
2.  **Log in to Heroku:** Open your terminal and run `heroku login`.
3.  **Create a Heroku App:** Navigate to your project's root directory (or `module09` if it's a subdirectory) and create a new Heroku app:
    ```bash
    heroku create your-app-name # Replace 'your-app-name' with a unique name
    ```
4.  **Build and Push Docker Image:** Build and push your Docker image to Heroku's Container Registry:
    ```bash
    heroku container:login
    heroku container:push web -a your-app-name
    ```
5.  **Release the Image:** Release the pushed image to deploy your application:
    ```bash
    heroku container:release web -a your-app-name
    ```
6.  **Open the App:** Open your deployed application in your browser:
    ```bash
    heroku open -a your-app-name
    ```

Remember to replace `your-app-name` with the actual name of your Heroku application.
