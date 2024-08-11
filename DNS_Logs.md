# DNS logs

![image](https://github.com/user-attachments/assets/771b96c1-4a58-456a-ba69-325f716e6f6f)

## Extract Relevant Fields

* source IP, destination IP, domain name, query type, response code, etc.


      index=* sourcetype=dns_sample | regex _raw="(?i)\b(dns|domain|query|response|port 53)\b"

