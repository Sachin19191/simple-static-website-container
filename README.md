# Project 2 - Set Up a Virtualized Environment Using Docker

## Prerequisites:
- An AWS Ubuntu instance (t2.micro) with SSH and HTTP traffic allowed in the security settings.
- Git and Docker installed on your instance.

## Steps to Set Up and Run the Dockerized Application:

1. **Connect to your AWS Ubuntu instance** using SSH:
    ```bash
    ssh -i <your-key-file>.pem ubuntu@<your-server-ip>
    ```

2. **Update and install dependencies**:
    - Check if Git and Docker are installed:
    ```bash
    sudo apt update
    sudo apt install git -y
    ```

3. **Clone the repository for the Dockerized web application**:
    ```bash
    git clone https://github.com/Sachin19191/simple-static-website-container.git
    cd simple-static-website-container
    ```

4. **Create the Dockerfile**:
    - In the project root directory, create a `Dockerfile` using vim or any text editor:
    ```bash
    vim Dockerfile
    ```
    - Add the following content:
    ```Dockerfile
    FROM nginx
    COPY . /usr/share/nginx/html
    ```

5. **Build the Docker image**:
    ```bash
    sudo docker build -t webapp .
    ```
    This will build the image with the name `webapp`.

6. **Run the Docker container**:
    ```bash
    sudo docker run -d -p 8080:80 --name mywebapp webapp
    ```
    - `-d`: Runs the container in detached mode (background).
    - `-p 8080:80`: Maps port 8080 on your local machine to port 80 inside the container.

7. **Test your application**:
    - Open your browser and visit your server's public IP with port 8080:
    ```
    http://<your-server-ip>:8080

    ```
### Live Testing
[3.6.160.37:8080](http://3.6.160.37:8080)
