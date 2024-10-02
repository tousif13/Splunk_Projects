# Splunk Use Cases

* Practical approach to investigate specific use cases using Splunk

##  `Geolocation or Users by Country`

    host=TousifMd
    | iplocation Src_IP
    | geostats dc(Src_IP) by Country

![image](https://github.com/user-attachments/assets/76aa85a7-3e13-4811-a737-92cd8e6587b0)

