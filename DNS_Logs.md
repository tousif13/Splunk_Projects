# DNS logs

Source : https://github.com/0xrajneesh/Splunk-Projects-For-Beginners/tree/main

![image](https://github.com/user-attachments/assets/ed28ecce-804d-4c05-9edc-9ea3c197a772)

## Extracting Fields

* Name some fields such as src_ip, dest_ip, domain etc for better understanding.
* ( Left pane ) Extract New Fields -> Select Sample Event -> Regex/Delimiters -> Add Extraction -> Finish

![image](https://github.com/user-attachments/assets/a870fd26-3f96-4d8b-91c4-6d2ab2c3aae7)

* Now it displays the extracted fields

![image](https://github.com/user-attachments/assets/96190d8b-8362-49d2-b319-39e2798aacb5)

* To extract DNS related logs, we could use below regex command

        index=* sourcetype=dns_log | regex _raw="(?i)\b(dns|domain|query|response|port 53)\b"

![image](https://github.com/user-attachments/assets/442468b2-d9ee-41f8-9942-73e6b2f7e6db)

      (?i): This makes the search case-insensitive.
      \b: This denotes word boundaries, ensuring the match occurs at whole words.
      (dns|domain|query|response|port 53): This is a list of words that are being matched. The | symbol is used as an OR operator in regex, so this regex will match any event that contains the words dns, domain, query, response, or port 53.


## Identify Patterns

### Displaying stats

        index=_* OR index=* sourcetype=dns_log  | stats count by Domain

![image](https://github.com/user-attachments/assets/5e82d460-7fbf-4942-8aa2-4ad203a3e5ff)

### Top command

        index=* sourcetype=dns_log | top Domain

![image](https://github.com/user-attachments/assets/eef3516f-a1fc-4268-990a-1a7a7fe74c01)

### Enumerating any malicious domain

        index=* sourcetype=dns_log Domain="<maliciousdomain>" | table Src_IP | dedup Src_IP

![image](https://github.com/user-attachments/assets/3d01ab1b-fb9e-4dfd-a680-5d31a7b65822)

        dedup is used to remove duplicate events from search results

