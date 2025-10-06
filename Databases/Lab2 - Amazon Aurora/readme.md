## Lab Description

- Create an AWS Aurora

---

- Engine selection

![alt text](image.png)

- Templates

![alt text](image-1.png)

- Database and credetials setup

![alt text](image-2.png)

- Cluster storage configuration

![alt text](image-3.png)

- Instance Classes

![alt text](image-4.png)

- Availability & durability

  - If you wish to have multi AZ. If you select either yes/no remember your storage layer is replicated across 3 AZs.

  ![alt text](image-5.png)

- Connectivity

![alt text](image-6.png)

![alt text](image-7.png)

- Database authentication

![alt text](image-8.png)

- Monitoring

![alt text](image-9.png)

![alt text](image-10.png)

- Additional

![alt text](image-11.png)

![alt text](image-12.png)

## After creating your Aurora Cluster

- You will see 2 endpoints.

  1. Writer endpint = Your main DB which has write + read. In your app use this endpoint.

  2. Reader = Only read purpose from main DB. For Analytical purpose use this READ only endpoint.

  ![alt text](image-13.png)

* More options

  ![alt text](image-14.png)

1. Creating auto scaling Read Replica policy

- Click "Add Auto Scaling policy"

  ![alt text](image-15.png)

  - It's tell you to add more read replica if the overall usage is >60%

- Minimum and Maximum Replica capacity

  ![alt text](image-16.png)

2. If you want to do Global Aurora. You can add a new AWS Region

   - Click "Add AWS Region" and create a new Aurora Cluster.
