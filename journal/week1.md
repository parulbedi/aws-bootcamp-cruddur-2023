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

## Running the following command to install the modules mentioned in requirements.txt file in backend-flask directory
### pip3 install -r requirements.txt
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_R5mbSMUXeF.png)

## Running backend on port 4567 port by enabling it to public
### python3 -m flask run --host=0.0.0.0 --port=4567
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_p2F34CRzF2.png)

### unlock the port 4567 by either clicking on make Public button or you can go the port tab and click on Lock icon to unlock the port
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_jB0vwJPqGn.png)

### Alternative way:
#### step: 1
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_cUIrL4ItvA.png)

#### step: 2
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_GkhPfiws6M.png)

## Building and then running container
### docker build -t  backend-flask ./backend-flask
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/building%20container.png)

