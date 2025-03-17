Prerequisites
Before you begin, ensure that you have the following tools installed:

1. Docker
Docker is needed to build, run, and manage containers.

Installation Guide: Docker Installation
Verify installation:
docker --version

2. Git
Git is needed to clone the repository to your local machine.

Installation Guide: Git Installation
Verify installation:
git --version



Clone the Repository
To get started, clone the repository to your local machine:

git clone https://github.com/SachinLulla/Particle41.git
Navigate into the project directory:

cd SimpleTimeService

Build the Docker Image
Once you've cloned the repository, you can build the Docker image using the following command:

docker build -t  simple-time-service .

where -t Task 1 Minimalist Application Development tags the image with the name simple-time-service.
This command may take a few minutes as it pulls the necessary dependencies.


Run the Docker Container

Once the image is built, you can run the Docker container. This will start the application on port 5000.

To run the container in the background:

docker run -d -p 5000:5000 simple-time-service
-d runs the container in detached mode (in the background).
-p 5000:5000 binds port 5000 of the container to port 5000 on your local machine.

Access the Application
After the container is running, you can access the SimpleTimeService by navigating to the following URL in your web browser:

📌 URL: http://localhost:5000