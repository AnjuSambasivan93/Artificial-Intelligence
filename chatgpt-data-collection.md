# ChatGPT: Data Collection and Technologies

## What is Data Collection?
Data collection is the process of gathering information from different sources to train AI models. OpenAI uses publicly available internet information, licensed datasets and human-provided data.

## How ChatGPT's Training Data Is Collected
- **Web Crawling:** Automated programs visit publicly accessible websites and retrieve information.
- **GPTBot:** A web crawler operated by OpenAI that collects publicly accessible web content for potential use in AI model development.
- **Licensed Datasets:** Information obtained through agreements with third-party organisations.
- **Human-Provided Data:** Information provided or created by users, trainers and researchers.

## Technologies Used
- **Web Crawlers:** Automated programs that discover and retrieve webpages.
- **HTTP/HTTPS:** Communication protocols used to request website content from web servers.
- **HTML Parsers:** Software that extracts text and links from webpage code.
- **Apache Spark:** A framework for processing large datasets across multiple computers.
- **Data Storage Systems:** Infrastructure used to store collected information before processing and training.

## How Web Crawling Works
1. A crawler starts with a website address (URL).
2. It checks crawling restrictions, such as `robots.txt`.
3. It requests webpage content using HTTP or HTTPS.
4. It extracts information and discovers links to other pages.
5. Collected information may be stored and prepared for AI training.

## Key Points
- Web crawling is one method of collecting training data.
- GPTBot is one of OpenAI's publicly documented web crawlers.
- Data collection happens before data cleaning and model training.
- Not every collected webpage becomes part of ChatGPT's training data.
- OpenAI has not disclosed every technology used in its current data collection pipeline.

## References
- [OpenAI – Overview of OpenAI Crawlers](https://platform.openai.com/docs/bots)
- [OpenAI – How ChatGPT and Our Foundation Models Are Developed](https://openai.com/policies/how-chatgpt-and-our-foundation-models-are-developed/)
