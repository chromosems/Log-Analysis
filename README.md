# Log-Analysis Challenge
# Instructions:
During a recent system compromise investigation, the Security Operations Center at Esquelle Eye Care discovered a critical oversight—the SIEM forwarding agent had never been installed on their corporate website's web server. This mistake left the web server's log data unmonitored.

A System Administrator managed to extract the Apache access log file from the server and has sent it to you for analysis. Your task is to review the challenge.log file to determine the extent of the compromise, its origin, the attack vector, and the vulnerability that led to the incident.

## Tools
- awk
- uniq
- grep
- tail
- head
- less
- more

## Skills Gained
- Tool profieciency
- Data Analysis and problem solving
- Incident Response and debugging

## Question 1
How many total events were logged in the file?
- Using wc, which is a count command the first digits are the total of lines on the log file, second are the words or characters and lastly the bytes
- <img width="616" height="86" alt="image" src="https://github.com/user-attachments/assets/96e4a718-0739-4dfd-989b-6a8c2ea25053" />

## Question 2
What is the full timestamp of the last event in the file?
- Using tail and tack n 1 to display the last line , 18/Jul/2024:15:59:25 -0400
- <img width="854" height="77" alt="image" src="https://github.com/user-attachments/assets/dbcf2c24-0851-477b-94c8-d1b7493c9583" />

## Question3 
What are the top 3 IP addresses found within the log file (in descending order)?
- To find the top three IP addresses , First we have to use cut and set a delimeter and filter only the IP address , onces the Ip address are outlined, then filter with sort -nr and uniq
- <img width="713" height="305" alt="image" src="https://github.com/user-attachments/assets/727a1a05-369c-40a9-83ce-6e91bad953f1" />
- Next, sorting the IPs to identify familiar patterns, duplicates and sort
- <img width="848" height="78" alt="image" src="https://github.com/user-attachments/assets/6e5e2192-da8f-4304-b4bb-ef28574ce49b" />

## Question 4
How many different user agent strings are found in the log file?
- First cut to user agents with "\"" -f 6 then Sort nr and uniq to filter
- <img width="772" height="57" alt="image" src="https://github.com/user-attachments/assets/f89d4607-5b68-4058-9689-c7465cbf6471" />
- The result has 3 outputs including Windows, Widows and Macintosh

## Question 5
Which user agent string sticks out as suspicious?
- adding tac -c to uniq gives account of duplications , but in this case, notice the spelling error, Legitimate Browesers dont misspell their own OOS identifiers
- <img width="765" height="96" alt="image" src="https://github.com/user-attachments/assets/c27aaaf8-b6b6-4392-aa00-70a233624e73" />

## Question 6
What is the line number of the log event that returned an HTTP status code of 404?
- Using the grep -n command with specified 404 code plus the log file , the result is shown as 76
- <img width="860" height="67" alt="image" src="https://github.com/user-attachments/assets/22c07736-caa7-4021-ba45-c32918a6bbaa" />

##  Question 7
What web-based attack can you identify based on the URL query parameters?
- lets extract the http request portion, results show attempts of sql injection
<img width="859" height="523" alt="image" src="https://github.com/user-attachments/assets/adc7d9ba-feb5-4515-9c60-4952e0cbc9ad" />


##  Question 8
What is the name of the vulnerable URL parameter?
- looking at the get blog/search.php , the q name holds the URL for all
-<img width="855" height="63" alt="image" src="https://github.com/user-attachments/assets/d1c3edaf-ebc7-425b-a7e1-dc5992a861d5" />

## Question 10
The attacker attempted a number of different SQL injection attacks. Based on other indicators in the event logs, what was the full timestamp of the potentially successful attempt?
- based on the URL, the sql command seems to be selecting from Users table which indicates the begining of a succeaful attack because the last command shows the a user name identified
- <img width="851" height="70" alt="image" src="https://github.com/user-attachments/assets/1a4f38cb-92f5-4ede-b6ed-7c257234d057" />

# Conclusion
Analyzing the provided log file allowed me to successfully identify anomalies, including a SQL injection attack, demonstrating the effectiveness of command-line log analysis for detecting security threats.






