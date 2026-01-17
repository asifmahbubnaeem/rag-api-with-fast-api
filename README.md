<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a RAG API with FastAPI

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-devops-api)

**Author:** asif naeem  
**Email:** asifnaim0123@gmail.com

---

![Image](http://learn.nextwork.org/delighted_chartreuse_swift_buddha's_hand_citron/uploads/ai-devops-api_g3h4i5j6)

---

## Introducing Today's Project!

In this project, I will demonstrate how to run a LLM locally based on a specific knowledgebase. I'm doing this project to learn how to build RAG API with FASTApi and build a production grade application that can be used for a specific knowledgebased question and answers.

### Key services and concepts

Services we used were ollama, uvicorn, FastAPI, chromaDB all these to build our RAG APIs. Key concepts we learnt include how RAG works, how APIs work, different types of endpoints and HTTP menthods and also testing our newly created endpoints both from terminal by curl command and from browser with swagger UI.

### Challenges and wins

This project took me approximately two hours. The most challenging part was understanding the chromadb embedding part of the project. It was most rewarding to test our extra endpoint (/add) to enrich our knowledge base dynamically.

### Why I did this project

We did this project because we wanted to build and AI api from the scratch also wanted to have hands on experience about RAG system, vectore db, knowledge base embedding.

---

## Setting Up Python and Ollama

In this step, I'm setting up Python and Ollama. Python is a popular programming language known for largely used for automation, AI, data analysis, web development. Ollama is and open source tool that let us run large language model in a personal computer.  I need these tools because I want to setup a LLM model in my personal computer based on a specific knowledge base also using python to build a web service API e that can interact with the LLM, we are using FASTapi which is a python based framework to API development.

### Python and Ollama setup

![Image](http://learn.nextwork.org/delighted_chartreuse_swift_buddha's_hand_citron/uploads/ai-devops-api_i9j0k1l2)

### Verifying Python is working

### Ollama and tinyllama ready

Ollama is a tool that let us run LLMs locally on our own computer. I downloaded the tinyllama model because this is perfect for learning and local development. The model will help our RAG API by running directly on our local machine and will power the AI responses. It's about 600MB, making it lightweight compared to larger models.

---

## Setting Up a Python Workspace

In this step, I'm setting up working environment by creating a project folder. I need it because everything in a project needs to be in the same place for a proper project structure and make it maintaninable. I also am going to create a python virtual enviroment so that our project specific dependencies can be separated from other projects. 

### Python workspace setup

### Virtual environment

A virtual environment is an isolated python environemnt that keeps our project's dependencies separate from other projects on the same system. It prevents conflict among multiple projects which might require the same package with different versions. I created one for this project to /Users/{USR_NAME}/Desktop/rag-api/rag-venv with following command: 
python3 -m venv rag-venv 
Once I activate it with To create a virtual environment, I can install all the required python packages under this folder
activate command:
source rag-venv/bin/activate
we can also check the packages created under this venv once the rag-venv is activated(we can name it with any name we want).
Check the installed packages with command:
pip3 list

### Dependencies

The packages I installed are : 
chromadb     v1.4.1
fastapi           v0.128.0
ollama           v0.6.1
uvicorn          v0.40.0

FastAPI is used for handling the incoming requests, interact with ollama and geenrate responses. 
Chromadb, a vector database is used for storing an retriving the vector embeddings of our project specific documents. It efficiently finds the most relevant information from our knowledge base by searching these embeddings. This relevant informations, or contenxt is then passed to the tinyllama model to generate an accurate answer.
Uvicorn is used for running our FastAPI application. It acts as the engine that powers our API, listening for incoming requests on our local machine and routing them to the correct functions in our code. It handles incoming requests making ours app accessible through API call or from browser.
Ollama is used for running the AI language models likes tinyllama directly on our machine.

![Image](http://learn.nextwork.org/delighted_chartreuse_swift_buddha's_hand_citron/uploads/ai-devops-api_u1v2w3x4)

---

## Setting Up a Knowledge Base

In this step, we are building a RAG API. RAG standas for retrival augmented generation. I am creating a knowledge base file with information about what is cucumber,  a knowledge based about running automated test. An API endpoint is an entry point to communicate with our API - requests go through these end points to retrive information from our knowledgebase.

### Knowledge base setup

![Image](http://learn.nextwork.org/delighted_chartreuse_swift_buddha's_hand_citron/uploads/ai-devops-api_t1u2v3w4)

### Embeddings created

Embeddings are numerical representations of text.  We have created them by rrunning the embed.py script. The db/ folder contains chroma database files. This is the db where the vector embeddings of our documents are stored. This is important for RAG because it helps to search relevant information efficiently.

---

## Building the RAG API

In this step, we are building a RAG API. An API is application programming interface, lets software retrieve and share data with other applications. FastAPI is a modern python framework used for building APIs. We are creating this because it simplifies the process of creating API. It handles the technical details of web requests and responses, allowing us to focus on the core logic of our RAG system.

### FastAPI setup

### How the RAG API works

Our RAG API works by seinding a questions to our server and breaking it down into embeddings using Chroma. Chroma will then compare the embeddings of our question with the embeddings of the documents stored in our knowledge base. The results for relevant information get passed as context to our tinyllama LLM along with the orginal question and the prompt to answer the question clearly based on the knowledge we have provided. The endpoint is /query and we have built it using HTTP POST menthod because we are sending the question to this API.

![Image](http://learn.nextwork.org/delighted_chartreuse_swift_buddha's_hand_citron/uploads/ai-devops-api_f3g4h5i6)

---

## Testing the RAG API

In this step, we are going to tes my RAG API. I'll test it using both from terminal and also from browser. Swagger UI is an interactive, web-based documentation for our API that is automatically generated by FastAPI. It allows us to visualize and interact with our API endpoints directly from browser.  I'll use it to show the API endpoints and also will run the query from browser in a more interactive mode.

### Testing the API

### API query breakdown

I queried my API by running the command  as follows:
curl -X POST "http://127.0.0.1:8000/query" -G --data-urlencode "q=what is cucumber?" 
The command uses the POST method, which means it sends the query as part of the request body and the question breaks down into embeddings which later on will be compared with our knowledge base embeddings and the reply will be prepared based on our knowledge base docs.
The API responded with :
{"answer":"Cucumber is a tool for running automated acceptance tests in plain language. It helps improve communication, collaboration, and trust among team members by making it easier to read and understand the tests and discuss their results with others."}
which is different from the question if we ask directly from terminal as follows:
Cucumbertree is a popular name in the world of art, culture, and fashion. It refers to a type of dried fruit that has 
a distinctive texture and taste. Cucumberts are typically made from dried cucumbers, which can range in si

![Image](http://learn.nextwork.org/delighted_chartreuse_swift_buddha's_hand_citron/uploads/ai-devops-api_g3h4i5j6)

### Swagger UI exploration

Swagger UI is an interactive, web-based documentation for our API that is automatically generated by FastAPI. We used it to test our query. The best part about using Swagger UI was it is more visual and easy to send the request only by posting the question.

---

## Adding Dynamic Content

In this project extension, we are going to build aother endpoint to update our knowledge base. This will enable us to dynamically add more information and based on that chroma db will be updated with new embeddings generatred from newly added knowledge base.

### Adding the /add endpoint

![Image](http://learn.nextwork.org/delighted_chartreuse_swift_buddha's_hand_citron/uploads/ai-devops-api_w9x0y1z2)

### Dynamic content endpoint working

The /add endpoint allows me to add new knowledge base. This is useful because we can enrich our knowledge base through API call and later can use this as new context.

---

---
