# altschool-cloud-project

# Url: https://planner.inkdeskng.org/
# public IP address: 16.171.147.54

# Screenshot of the HTML page in the browser
![landing-page-scre](https://github.com/user-attachments/assets/c02042ca-a627-48d4-a22f-b665a1fb8e11)

# Step-by-step documentation of Deploying/building a simple HTML page on a Linux Server with AWS as the cloud provider

# Step 1:
We need to build an Ec2 Instance (Use the search bar to get quick access to EC2) 
Once you click on it, next will be to click on Launch instance, 
- Select Ubuntu as the AMI (Amazon Machine Image) 
- Select the Instance type, in my case I used the t3.micro that has the *eligible for free tier* to it
- You can use default settings for configure instance details,
- Make sure to configure the security group, i did more configuration after i had launched the instance
- then launch, make sure you keep the .pem file very safe, that's what we will use to SSH into the linux server created in the instance.

# Let's Connect to the Instance

We will use the key to ssh into the ubuntu server with the public ip, it will be like this:
*ssh -i the.pem-key.pem ubuntu@<public-ip>*

# Step 2:
Let's run some linux command after we have connected to the server
*sudo apt update
sudo apt upgrade -y
sudo apt install nginx -y*

After installing the nginx we will enable and start the nginx service:
*sudo systemctl start nginx
sudo systemctl enable nginx*

# Step 3:
Let's create the HTML file, 
- First we will navigate to nginx root directory (cd /var/www/html)
- then sudo nano index.html to add the html content
- After adding the content: ctrl + x to save and exit by following the instruction.

You can verify the content of the web page through the public IP address: 
http://<your-public-ip>

# Let's get it to have SSL 
We will first make sure there's a subdomain or domain we want to use, point your public domain to the A records of the domain/sub-domain
After this, let's install Certbot:
*sudo apt install certbot python3-certbot-nginx -y*

then after a successful installation the obtain the certificate and put in thee domain or sub domain name, just follow the prompts
*sudo certbot --nginx* 

# Note: Before verifying, make sure there's an inbound rule for HTTPS and port 443

Now you can Verify if the HTTPS works by visiting the url: https://thesubdomain.com or https://domain.com.




