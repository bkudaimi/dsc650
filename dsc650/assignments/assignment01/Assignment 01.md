---
title: Assignment 1
subtitle: Computer performance, reliability, and scalability calculation
author: Bilal Kudaimi
---

## 1.2 

#### a. Data Sizes

###Calculations

####1. A 128 character message is about 128 bytes because each character in ASCII is represnted by 1 byte.

####2. A 1024x768 PNG image contains 786,432 pixels, and each pixel contains 3 bytes of data (one for each color of RGB). 786,432(3) = 2,359,296 bytes per 1024x768 PNG image, or about 2.3 MB.

####3. 

####4. According to this source (http://phenix.it-sudparis.eu/jct/doc_end_user/current_document.php?id=7746), HEVC has up to a 1000:1 compression ratio. Since the video is just the video in #5 but compressed, the size of this video will be 1000 times smaller than the video in #5 at maximum, which is about 160 MB.

####5. To calculate how large a video is, we must multiply the number of frames by the size of each frame. This video is 15-minutes at 30 fps so there are 27,000 frames. Each frame is 1080p meaning it is 1920x1080, or 2,073,600 pixels. Each pixel contains 3 bytes as previously mentioned, meaning that each frame has 2,073,600(3) = 6,220,800 bytes or 5.9326 MB. Multiplying 5.9326 MB/frame by 27,000 frames, we get 160,180 MB per 15-minute 1080p video at 30 fps. 

####6. Because HEVC can compress videos to 1/1000 of their original size, the size of a 4K HEVC video 15-minutes long is about 641 MB.

####7. Once again, we will multiply the number of frames by the size of each frame. We again have 27,000 frames since it is still 15-minutes at 30 fps. The frame size has now increased, however, since the resolution is now 4K (3840x2160). A 4K frame has 4x the number of pixels as 1080p, or about 8,294,400 pixels. With each pixel having 3 bytes of data, 8,294,400(3) = 24,883,200 bytes or 23.73 MB per frame. Multiplying 23.73 MB/frame by 27,000 frames, we get 640,710 MB per 15-minute 4K video at 30 fps.

####8. The human genome is made up of a strand of 3 billion bases. The four bases can be represented with 2 bits (00, 01, 10, or 11). 3,000,000,000(2) = 6,000,000,000 bits in the human genome, which is 750,000,000 bytes or 715 MB. Each cell contains 2 copies, however, so the in vivo size per cell would be 715(2) = 1430 MB or 1.396 GB. 
| Data Item                                  | Size per Item | 
|--------------------------------------------|--------------:|
| 128 character message.                     | 128 Bytes     |
| 1024x768 PNG image                         | 2.3 MB        |
| 1024x768 RAW image                         | ? MB          | 
| HD (1080p) HEVC Video (15 minutes)         | 160 MB        |
| HD (1080p) Uncompressed Video (15 minutes) | 160,180 MB    |
| 4K UHD HEVC Video (15 minutes)             | 641 MB        |
| 4k UHD Uncompressed Video (15 minutes)     | 640,710 MB    |
| Human Genome (Uncompressed)                | 1.396 GB      |

#### b. Scaling

###Calculations
####The estimates from the previous part will be used in this part.

####1. About 500 million tweets are sent daily. We can assume each tweet is a 128-character message (128 B) so 500,000,000(128) = 64E9 bytes or 59.6 GB of tweets uploaded daily. This will need 1 10TB hard disk to store the data and accommodate the HDFS. 

####2. Snappy has a compression ratio of about 1.5x for text, so for the daily tweets, this would be 59.6/1.5 = 39.7 GB. This will need 1 10TB hard disk to store the data and accommodate the HDFS. 

####3. About 100 million photos and videos are uploaded to Instagram each day, and we can assume 75%, or 75 million, are 1024x768 PNG photos (2.3 MB). Therefore, 75,000,000(2.3) = 172,500,000 MB or 164.51 TB of photos uploaded to Instagram daily. This will need 51 10TB hard disks to store the data and accommodate the HDFS.

####4. About 500 hours of video is uploaded to YouTube every minute, or 720,000 hours daily. We can assume these videos are all 1080p HEVC at 30 fps (160 MB per 15 minutes or 640 MB per hour), so 720,000(640) = 460,800,000 MB or 439.45 TB of videos uploaded to YouTube daily. This will need 132 10TB hard disks to store the data and accommodate the HDFS. 

####5. We can simply multiply the daily twitter tweet size from #1 by 365 to get the annual uploaded tweet size, so 59.6(365) = 21,754 GB or 21.24 TB of tweets per year. This requires 9 10TB hard disks to store the data and accommodate the HDFS.

####6. We can simply multiply the compressed daily tweet size from #2 by 365 to get the annual compressed tweet size, so 39.7(365) = 14,491 GB or 14.15 TB of compressed tweets per year. This requires 6 10TB hard disks to store the data and accommodate the HDFS.

####7. We can simply multiply the daily Instagram photo size from #3 by 365 to get the annual uploaded Instagram photo size. 164.51(365) = 60,046.15 TB or 58.64 PB of Instagram photos per year. This requires 18,015 10TB hard disks to store the data and accommodate the HDFS.

####8. We can simply multiply the daily YouTube video size from #4 by 365 to get the annual uploaded YouTube video size. 439.45(365) = 160,399.25 TB or 156.64 PB of YouTube videos per year. This requires 48,120 10TB hard disks to store the data and accommodate the HDFS.  
|                                           | Size     | # HD | 
|-------------------------------------------|---------:|-----:|
| Daily Twitter Tweets (Uncompressed)       | 59.6 GB  |     1|
| Daily Twitter Tweets (Snappy Compressed)  | 39.7 GB  |     1|
| Daily Instagram Photos                    | 164.51 TB|    51|
| Daily YouTube Videos                      | 439.45 TB|   132|
| Yearly Twitter Tweets (Uncompressed)      | 21.24 TB |     9|
| Yearly Twitter Tweets (Snappy Compressed) | 14.15 TB |     6|
| Yearly Instagram Photos                   | 58.64 PB |18,015|
| Yearly YouTube Videos                     | 156.64 PB|48,120|

#### c. Reliability

####The Backblaze estimated hard drive failure rate (annualized for 2021) is 1.1%, so each number of hard drives was multiplied by 0.011 to get the number of failures per year.
|                                    | # HD | # Failures |
|------------------------------------|-----:|-----------:|
| Twitter Tweets (Uncompressed)      |     9|          <1|
| Twitter Tweets (Snappy Compressed) |     6|          <1|
| Instagram Photos                   |18,015|        ~199|
| YouTube Videos                     |48,120|        ~530|

#### d. Latency

####The latency between Los Angeles and Amsterdam was obtained from this source: https://wondernetwork.com/pings/Amsterdam/Los%20Angeles. The latency was cut in half to get the one-way latency.

####The satellite latency information was obtained from this source: https://www.telesat.com/wp-content/uploads/2020/07/Real-Time-Latency_HW.pdf. The average latencies were cut in half to get the one-way latencies.

####The planetary latency information (Earth to Moon and Earth to Mars) was obtained from this source: https://www.spaceacademy.net.au/spacelink/commdly.htm. These times are one-way latency times.
|                           | One Way Latency      |
|---------------------------|---------------------:|
| Los Angeles to Amsterdam  | 70.7 ms              |
| Low Earth Orbit Satellite | 20 ms                |
| Geostationary Satellite   | 350 ms               |
| Earth to the Moon         | 1,300 ms             |
| Earth to Mars             | 21 minutes           | 
