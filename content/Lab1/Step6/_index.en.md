---
title: "Step 6. Visit your website and configure the WordPress setting"
chapter: false
weight: 30

---

* Visit [**IAM console**](https://console.aws.amazon.com/iam/home?region=us-east-1#/home)
* Click **Users** on the left menu, then click **Add user** 
* Enter `Wordpress` in **username**
* For **Select AWS access type**, select **Programmatic access** and click **Next: Permissions**
* For **Set permissions**, select **Attach existing policies directly** Search and attach **CloudFrontFullAccess** and **AmaoznS3FullAccess** 
* Click **Next: Tags** → **Next: Review** → **Create user** 
* Click **Download .csv** to store your Access/Secret key

![](/images/lab1-16.png)

![](/images/lab1-17.png)

![](/images/lab1-18.png)

![](/images/lab1-19.png)


* Open another tab/window and visit [**EC2 console**](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Instances:sort=instanceId)
* Select the EC2 instance, and find the **Public IPv4 DNS** in **Details** below and paste it on your browser, then you will see the setup page of WordPress.

![](/images/lab1-20.png)

* In setup page, enter your own value in the **Site Title**, **Username**, **Password** and **Your Email**, then click **Install WordPress**
    
![](/images/lab1-21.png)

* After few seconds, it will be redirected to Login page, 
* Enter your **username** and **password**, and click **Login** button, you will see the **admin** page,
* In admin page, click **Plugins** on the left menu, 
* Click **Add New**, search `wp offload media lite` and click **Install Now → Activate**,
* Click **Settings** on the left menu, 


![](/images/lab1_22_wp_plugin_offload_media_install.png)

* In **Offload Media Lite**,
* Choose **Storage Provider**
* Choose **I understand the risks but I'd like to store access keys in the database anyway**
* Now add the **Access Key ID** and **Secret Access Key**  
* Click **Next**

![](/images/lab1_23_access_key_secret_key.png)

* Choose to **Create Bucket** at the bottom of the screen, it will open up a new screen
* Add ``wp-workshop-wordpress-yourfirstnamelastname``
* Then click on **Create New Bucket**

![](/images/lab1_23a_create_bucket.png)

* Since we are not using CloudFront just yet, we need to click **Disable "Block Public Access"**
![](/images/lab1_23b_block_all_public_access.png)

* Click **Performance/CDN** on the left menu, scroll down to find **Configuration: Objects** section 
* Copy and paste the **Access key ID** and **Secret key** from IAM user creation page
* For **Bucket**, enter `wp-workshop-<custom name>` and click **Create as new bucket**
* Click **Test S3 upload** to ensure connection succeeded and click **Save all Settings**

![](/images/lab1-27.png)


* Click the **Page/All pages** on the left menu, click **Simple page** to edit it click “+” icon on the top left and insert a sample image, then click **Update** to confirm the change. [download sample image](https://d1.awsstatic.com/logos/aws-logo-lockups/poweredbyaws/PB_AWS_logo_RGB_REV_SQ.8c88ac215fe4e441dc42865dd6962ed4f444a90d.png)
* Click **Performance/CDN** the left menu and click **export the media library, wp-includes, theme files**  
* Click **custom files → start** button to export file from EC2 to S3 bucket

![](/images/lab1-24.png)

![](/images/lab1-25.png)

* Now, you can view your sample page in `<your ec2 domain>/index.php/sample-page/`
    
![](/images/lab1-26.png)
