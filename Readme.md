# ***Data Pricing Evaluation***
- This is the dataset for researching "Data pricing evaluation" in IBD Lab(University of Seoul)
- Listed source codes are data ETL pipelines from various data marketplace in Korea into our dataset

# ***Data sources***
- KDX(https://kdx.kr/main)
- Data Open Market(https://www.bigdata-transportation.kr/)
- BigDataSea(https://www.bigdata-sea.kr/)

# ***Data description***
- 대분류, 중분류, 소분류
  - We first have define top 1000 tags based on wordcount with entire data
  - Next, we asked ChatGPT(community edition) to define category group from the top 1000 tags
  - Using ollama and exaone3.5:32b(https://ollama.com/library/exaone3.5), we asked it to match category for each data
  - If it does not matched to appropriate category, tried again until it matches correctly or else leaved as "etc"
- price
  - If the actual price is "Free" from original data then converted as "0" in this price column
  - In some cases, the pricing information is not given
    - It is different from "Free of charge"
    - In this case price is -1 which means "Invalid or Not given"    
- data_size
  - The original information in the datasheet of each dataset
- data_size_bytes
  - In some cases, the "data_size" is given as "row count"
    - We can estimate data size in byte by multiplying "row count" and "average row bytes of gievn sample"
  - In some cases, the exact size of data is not given
    - -1: "Unknown size"
