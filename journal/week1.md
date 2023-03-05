# Week 1 — App Containerization

## Learned about Docker and Dockerfile, and how it works (its layer by layer architecture)

### Host OS/ Guest OS Concept
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/hosted-hypervisor.png)

## Change current working directory to backend-flask
### cd backend-flask/
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_MSjFtJCQAY.png)

## Exporting frontend & backend urls
### export FRONTEND_URL="*"
### export BACKEND_URL="*"
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_IU3mtHe0ct.png)

## Running backend on port 4567 port by enabling it to public
### python3 -m flask run --host=0.0.0.0 --port=4567

## Building and then running container
docker build -t  backend-flask ./backend-flask
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/building%20container.png)

