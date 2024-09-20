# DNS logs

Source : https://github.com/0xrajneesh/Splunk-Projects-For-Beginners/tree/main

![image](https://github.com/user-attachments/assets/ed28ecce-804d-4c05-9edc-9ea3c197a772)

## Extracting Fields

* source IP, destination IP, domain name, query type, response code, etc.


      index=* sourcetype=dns_sample | regex _raw="(?i)\b(dns|domain|query|response|port 53)\b"

