## Lab Description

- In this section we setup 3 EC2 web server instances.

---


## EC2

- Each EC2 must be in separate region AZ

    ![alt text](image-1.png)

    ![alt text](image-2.png)

    ![alt text](image-3.png)

    - User data

        ```
        #!/bin/bash
        yum update -y
        yum install -y httpd
        systemctl start httpd
        systemctl enable httpd
        echo "<h1>Hello from $(hostname -f)</h1>" > /var/www/html/index.html
        ```

    - EC2 instances (I renamed them in an incremental order)

        - IP: 13.204.82.210 (ap-south-1b)

        ![alt text](image-4.png)
        
        - IP: 35.175.175.177 (us-east-1c)

        ![alt text](image-5.png)

        - IP: 52.59.207.32 (eu-central-1b)

        ![alt text](image-6.png)


## ALB
- ALB: Now let's create an ALB in eu-central-1b. For the target group I will provide the eu-central-1b EC2 (webserver-3)

    ![alt text](image-7.png)

    - New SG for ALB

        ![alt text](image-8.png)

    ![alt text](image-9.png)

    - New target group

        ![alt text](image-10.png)

        - webserver-3 instance added to target group

            ![alt text](image-11.png)
    
    ![alt text](image-12.png)

## Results

- Asia Pacific: 13.204.82.210 (ap-south-1b)

    ![alt text](image-13.png)

- United States: 35.175.175.177 (us-east-1c)

    ![alt text](image-14.png)

- Europe: 52.59.207.32 (eu-central-1b)

    ![alt text](image-15.png)

- ALB (Europe) [webserver-alb-1324482464.eu-central-1.elb.amazonaws.com](webserver-alb-1324482464.eu-central-1.elb.amazonaws.com)

    ![alt text](image-16.png)



### Table

| Region        | IP Address     | Availability Zone | Notes                                                                 |
|----------------|----------------|-------------------|------------------------------------------------------------------------|
| Asia Pacific   | 13.204.82.210  | ap-south-1b       | —                                                                      |
| United States  | 35.175.175.177 | us-east-1c        | —                                                                      |
| Europe         | 52.59.207.32   | eu-central-1b     | —                                                                      |
| ALB (Europe)   | —              | —                 | [webserver-alb-1324482464.eu-central-1.elb.amazonaws.com](http://webserver-alb-1324482464.eu-central-1.elb.amazonaws.com) |
