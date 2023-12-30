# 1. Proposal (10/30)

1. Problem definition⚡
   - What is Website fingerprinting?

2. Data analysis and pipeline🛠
   - Data overview

3. Candidate features🎨
   - Which features will we explore and why?

4. Model introduction🔑
   - What models will we explore and why?

5. Else🔍
   - Tuning, preliminary results, experimental scenario, etc

References

- [Wang et al. Effective Attacks and Provable Defenses for Website Fingerprinting. Usenix Security14.](https://file.notion.so/f/f/ba8e00c2-fec6-4186-ac41-8f215ba31d9b/89d3652a-66ef-4669-af0c-370586369774/trafficsliver-ccs2020.pdf?id=36e51d05-5622-44f5-9842-b8da7905f038&table=block&spaceId=ba8e00c2-fec6-4186-ac41-8f215ba31d9b&expirationTimestamp=1697436000000&signature=C7mU0hlfcF1-ij8TYo9H7NH-v0Bo4n1yUW1adK1nzw0&downloadName=Cadena+et+al.+TrafficSliver%3A+Fighting+Website+Fingerprinting+Attacks+with+Tr%0Aaffic+Splitting.+CCS20.pdf)

- [Hayes and Danezis. k-fingerprinting: A Robust Scalable Website Fingerprinting Technique. Usenix Security16.](https://file.notion.so/f/f/ba8e00c2-fec6-4186-ac41-8f215ba31d9b/b133694c-5e82-45b2-83cd-e938ac42fddb/1801.02265.pdf?id=020ff24e-4f42-43ce-b578-1e34ab215ff5&table=block&spaceId=ba8e00c2-fec6-4186-ac41-8f215ba31d9b&expirationTimestamp=1697436000000&signature=u90-yB4PKYNDCq60dcxuKXuYC1a-8jH9d4disu0u_F8&downloadName=Sirinam+et+al.+Deep+Fingerprinting%3A+Undermining+Website+Fingerprinting+D%0A.pdf)

- [Panchenko et al. Website Fingerprinting at Internet Scale. NDSS16](https://file.notion.so/f/f/ba8e00c2-fec6-4186-ac41-8f215ba31d9b/a9762c13-4bd7-4f3d-8277-3ac1eb6c7401/fingerprinting-ndss2016.pdf?id=5975bae7-629c-4b7f-a347-f634c67e1fcd&table=block&spaceId=ba8e00c2-fec6-4186-ac41-8f215ba31d9b&expirationTimestamp=1697436000000&signature=FCxkknAfyHe6zmRwFltJcdPnXJYw7r-zfYVEYkWOvJc&downloadName=Panchenko+et+al.+Website+Fingerprinting+at+Internet+Scale.+NDSS16%0A.pdf)

- [Sirinam et al. Deep Fingerprinting: Undermining Website Fingerprinting Defenses with Deep Learning. CCS18](https://file.notion.so/f/f/ba8e00c2-fec6-4186-ac41-8f215ba31d9b/8594dce3-6f9b-494f-9c19-05c7cdc9f6c8/sec16_paper_hayes.pdf?id=d7c484cb-7a71-4946-ab65-0550f8f5f657&table=block&spaceId=ba8e00c2-fec6-4186-ac41-8f215ba31d9b&expirationTimestamp=1697436000000&signature=XSq3_X2pYgpQ-9cAErzS1MVdrst_a6eNJwBE3z-VxuA&downloadName=Hayes+and+Danezis.+k-fingerprinting%3A+A+Robust+Scalable+Website+Fingerpri%0Anting+Technique.+Usenix+Security16.%0A.pdf)

- [Cadena et al. TrafficSliver: Fighting Website Fingerprinting Attacks with Traffic Splitting. CCS20](https://file.notion.so/f/f/ba8e00c2-fec6-4186-ac41-8f215ba31d9b/07875574-85c3-4120-9b9b-e38dc5b83222/sec14-paper-wang-tao.pdf?id=b78e6eee-6cad-4851-8398-4e3621e258e9&table=block&spaceId=ba8e00c2-fec6-4186-ac41-8f215ba31d9b&expirationTimestamp=1697436000000&signature=jk0Yqh5tY6eZUqMaEyDobhMp7BQacGIm5kT2GzDyLaM&downloadName=Wang+et+al.+Effective+Attacks+and+Provable+Defenses+for+Website+Fingerpri%0Anting.+Usenix+Security14..pdf)

# 2. Final Presentation (12/11)
Problem Statement
This project focuses on website fingerprinting within anonymous networks, aiming to develop a robust model for accurately identifying monitored & unmonitored websites in both closed-world and open-world scenarios. The method includes collecting website traffic data and undergoing a training process using machine learning techniques, utilizing features such as packet size, packet direction, and timestamp. The project has two main objectives:
1.	Closed-World Website Fingerprinting:

  	•	Objective: Classify 95 monitored websites.
2.	Open-World Website Fingerprinting:
(1) Binary Classification:

  	•	Distinguish between monitored and unmonitored websites
(2) Multiclass Classification:

  	•	Further classify monitored websites into 95 classes (0 to 94), along with a category for unmonitored websites (-1).
3.	Data Analysis:
By focusing on significant features and leveraging a structured data analysis approach, before designing a website fingerprinting model for anonymous online communication.

  	•	Data Definition: The dataset includes features such as timestamps, packet directions, packet sizes (512 bytes), for both monitored (95 websites with 10 subpages observed 20 times each, total of 19,000 instances) and unmonitored (10,000 instances) websites. Monitored websites includes ‘site of each instances’(95 websites).

  	•	Data Preprocessing: 

  	   a) Data Transformation:

  	      •	Four continuous features (feature1-4 in order - Array to store instances (timestamps), array to store instances (direction*size), array to store bursts, and array to store cumulative packet sizes)

  	      •	11 categorical features have been added (feature5-15) - such as the number of incoming and outgoing packets, standard deviation, and averages of packet ordering. Each of the features were converted from continuous feature, feature2.

  	      •	Referred to the paper "k-fingerprinting: A Robust Scalable Website Fingerprinting Technique. Usenix Security16"
  
   b) Data Reduction:
        
         •	To simplify the model and prevent overfitting, less-contributing features were removed. 
       
         •	From monitored websites, we extracted feature5-17(but feature 10 and 13 were difficult for us to figure out how to make them. But since we decided to remove some of the features concerning overfitting, we figured it won’t have much of an impact on the results(예상질문 답변내용) and examined the feature importance. 
        
         •	We had a slight issue with feature 1-4, which turned out that the array format of features extracted from each instance couldn’t decide it’s importance. So we updated feature (timestamps) and feature3-bursts to assign just 1 value for each instance(feature2 and 4 were not able to extract 1 value). From feature 1, we sorted the largest interval between timestamps in each instance's list of timestamps. In Feature 3, we chose the maximum value among the sizes(absolute value) of each instance’s burst list. (예상질문 답변내용)
        
         •	Finally, from updated features (- feature 1*,3*,4-9,11-12 and 14-17), we computed their feature importance.
        
         •	Feature importance analysis identified features 1, 5, 9, 6, 7, 14, and 12 as crucial (feature importance > 0.1).
        
         •	This table represents features in order of their importance.
1	Feature 1	Array to store instances (timestamps)
2	Feature 5	Number of incoming packets
3	Feature 9	Number of outgoing packets
4	Feature 6	Number of outgoing packets as a fraction of the total number of packets
5	Feature 7	Number of incoming packets as a fraction of the total number of packets
6	Feature 14	Total number of packets
7	Feature 12	Sum of incoming, outgoing and total number of packets


• In conclusion, we selected total 7 significant features for the machine learning algorithm to classify websites using those features.

