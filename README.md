
21bds028-Kiriti Kumar Kola (KOLAKIRITI)
21bds032-Satyam Kunche
21bds035-M Ruthvik (Ruthvik-7)
21bds042-N Dilli Babu (Dillideekshi)



https://github.com/Dillideekshi/cloud-.git



Step 1: Start EC2 (Ubuntu 22.04):

Provision an EC2 instance on AWS with Ubuntu 22.04.
Connect to the instance using SSH.
Step 2: Clone the code:

Update all packages and then clone the code.

Clone your app's code repository to an EC2 instance:

``` bash
git clone https://github.com/Dillideekshi/cloud-.git
```

Step 3: Install Docker and run the application using the container:

Set up Docker on an EC2 instance:

``` bash
sudo apt-get update
sudo apt-get install docker.io -y
sudo usermod -aG docker $USER # Replace with your system username, eg 'ubuntu'
newgrp docker
sudo chmod 777 /var/run/docker.sock
```

Build and run your application using Docker containers:

``` bash
cd cloud
docker build -t netflix .
docker run -d --name netflix -p 8081:80 netflix:latest
```

To delete a container and an image:

``` bash
docker stop <containerid>
docker rmi -f netflix
```

Step 4: Get API Key:

Open a web browser and go to the TMDB (The Movie Database) website.
Click "Sign In" to create an account.
After logging in, go to your profile and select "Settings".
Click on "API" on the left panel.
Click "Create" and accept the terms and conditions to create a new API key.
Enter the required basic information and click "Submit".
You will receive your TMDB API key.
Now build the Docker image again using the API key:

``` bash
docker build --build-arg TMDB_V3_API_KEY=<api-key> -t netflix .
```

Replace "<your-api-key>" with the API key you got from TMDB.
