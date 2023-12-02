# Docker Dev Setup for CodeIgniter projects

## Local dev guide (Linux)

1. Clone the repo:
    ```.sh
    git clone https://github.com/TOA-Anakin/codeigniter-docker-dev.git
    ```
2. Rename the cloned repo as desired: 
    ```.sh
    mv codeigniter-docker-dev your_project_name
    ```
3. Check your user ID using the `id -u` command and update the `.docker/.env` file accordingly.
4. `cd` into the `.docker` directory and build the Docker containers:
    ```.sh
    cd your_project_name/.docker
    docker compose up -d --build
    ```
    Before the end of the process you should see a list of newly created (now running) containers:
    ```.sh
    [+] Running 5/5
    ✔ Network codeigniter_docker_dev_app
    Created                                      0.2s 
    ✔ Volume "codeigniter_docker_dev_db"
    Created                                      0.0s 
    ✔ Container codeigniter_docker_dev-phpmyadmin-1
    Started                                      0.2s 
    ✔ Container codeigniter_docker_dev-db-1
    Started                                      0.2s 
    ✔ Container codeigniter_docker_dev-nginx-1
    Started                                      0.2s
    ```
5. Open the terminal of the server container (mine is named `codeigniter_docker_dev-nginx-1`) and create a CodeIgniter project using `composer`:
    ```.sh
    docker exec -it codeigniter_docker-nginx-1 bash
    composer create-project codeigniter4/appstarter tmpdir
    ```
    Move the contents of `tmpdir` into the project root:
    ```.sh
    mv tmpdir/* . && mv tmpdir/.[!.]* . && rmdir tmpdir
    ```
6. Access your CodeIgniter web app at http://localhost