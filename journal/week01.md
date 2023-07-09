# Week 1 — App Containerization

## Learned about Docker and Dockerfile, and how it works (its layer by layer architecture)

### Host OS/ Guest OS Concept
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/hosted-hypervisor.png)

## Change current working directory to backend-flask
### cd backend-flask/
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_MSjFtJCQAY.png)

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

### Click on the link (it will show 404 error)
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_U50j61znRv.png)

### Appemd api endpoint "/api/activities/home" to your gitpod url link as below (it will show 500 server error)
#### https://4567-parulbedi-awsbootcampcr-oql1596g36l.ws-us89.gitpod.io/api/activities/home

## Exporting frontend & backend urls
### export FRONTEND_URL="*"
### export BACKEND_URL="*"
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_IU3mtHe0ct.png)


## Restart backend on port 4567 port
### python3 -m flask run --host=0.0.0.0 --port=4567
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_jKoQCslYmV.png)


### Visit the link again and this time you will get a response in form of json
#### https://4567-parulbedi-awsbootcampcr-oql1596g36l.ws-us89.gitpod.io/api/activities/home

![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_ppznGYjLWf.png)

## Unset the env vars:
### unset FRONTEND_URL
### unset BACKEND_URL
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_tw1gPb1AzH.png)


## Building and then running container

#### make sure that you are at root directory

### Building container
### docker build -t  backend-flask ./backend-flask
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_UdK1Ik7yrc.png)
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/building%20container.png)

### Running container
### docker run --rm -p 4567:4567 -it backend-flask
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_o2Xtlq9Ww7.png)

### It will through 404 error as Environment variables are yet not set
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_sqAuSuGTyy.png)

### api endpoints also return error (need to set env vars)
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_fHKyTyjCJq.png)

### setting environment varibales and running container again
### docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_s4lH5mxhgN.png)

### this time you will get a response in form of json
#### https://4567-parulbedi-awsbootcampcr-lqhbj29hyja.ws-us89b.gitpod.io/api/activities/home
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_5J8ztKjXju.png)

### change working directory to frontend-react-js directory
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_dKS7Y7y4U8.png)

### install npm package
### npm i
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_wHt6autovk.png)

### create Dockerfile in frontend-react-js directory
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_JsqyAdYHlR.png)

### add the following script in Dockerfile
```dockerfile
FROM node:16.18

ENV PORT=3000

COPY . /frontend-react-js
WORKDIR /frontend-react-js
RUN npm install
EXPOSE ${PORT}
CMD ["npm", "start"]
```

![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_pqZB8d46Gi.png)

### change directory to root folder
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_SZy72LnFv7.png)

### build container
### docker build -t frontend-react-js ./frontend-react-js
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_H504qNYmVy.png)


### run container
### docker run -p 3000:3000 -d frontend-react-js
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_mfviHgPvLJ.png)

### unlock port 3000, Just go the port tab and click on Lock icon to unlock the port
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_IQ4fVDlhJd.png)


### Create a file with name docker-compose.yml

```yaml
version: "3.8"
services:
  backend-flask:
    environment:
      FRONTEND_URL: "https://3000-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
      BACKEND_URL: "https://4567-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
    build: ./backend-flask
    ports:
      - "4567:4567"
    volumes:
      - ./backend-flask:/backend-flask
  frontend-react-js:
    environment:
      REACT_APP_BACKEND_URL: "https://4567-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
    build: ./frontend-react-js
    ports:
      - "3000:3000"
    volumes:
      - ./frontend-react-js:/frontend-react-js

# the name flag is a hack to change the default prepend folder
# name when outputting the image names
networks: 
  internal-network:
    driver: bridge
    name: cruddur
```

### to start the application run the following command
### docker-compose up
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_cx5NDFbGxy.png)


### goto the ports tab and click on the link correspond to port 3000
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_cmb0DIIu7u.png)


### verify that the below highlighted data is visible when opening link, if no data is shown in this area,
### then you may need to remove the containers running on port 4567 & 3000
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/kCIBgcAn4U.png)


### frontEnd of cruddur app is running which is communitcating with backEnd on port 4567
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_Hvi28VcqXI.png)

### Notification API endpoint is working
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_kqs3k8vm0L.png)

### Notification page is working
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_95HUmjgUx5.png)

### DynamoDB Local Container is running
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_vFFug36jY4.png)

### Postgres Container is running
![Architecture image](https://github.com/parulbedi/aws-bootcamp-cruddur-2023/blob/main/screenshots/msedge_0Bqlo2OHsp.png)
