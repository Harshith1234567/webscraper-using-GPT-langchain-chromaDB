# webscraper-using-langchain-and-chromaDB

This is a small demo project illustrating a chatbot that can query a scraped website. It uses LangChain to manage the chatbot's framework, Gradio for a user friendly interface, OpenAI's `gpt-3.5-turbo` LLM model, and ChromaDB as a vector store. 

![image](https://github.com/Harshith1234567/webscraper-using-langchain-and-chromaDB/assets/53342028/782242d1-d2fa-432f-a5f8-67d311befa4b)

## Getting started

This project supports both `pip` and `pipenv`. I recommend using `pipenv` for the best (and least error prone) experience.

### Installation

#### Pip
Run 

```bash
pip install -r requirements.txt
```

if using `pip`.

#### Pipenv

Run

```bash
pipenv install
```

if using `pipenv`, followed by `pipenv shell` to start a shell with the installed packages.

### Environment variables

We need to create a new `.env` file from the `.env.example` file with our `OPENAI_API_KEY`. We can create one of these on OpenAI's platform. 

### Web scraping

To scrape a site, run 

```
python scrape.py --site <site_url> --depth <int>
```

This will scrape a url and all links found at that url recursively up to the specified `depth`. This will only scrape sites with the same origin as the given `<site_url>`, so for example scraping `https://python.langchain.com/docs` will only scrape sites at `https://python.langchain.com`.

The data will be stored in a new `scrape/` directory.

### Data embeddings

To generate and persist the embeddings and create a vector store, run

```bash
python embed.py
```

A new persisted vector store will be created in the `chroma/` directory.

### Launching the chatbot

To launch the chatbot, we need to run

```bash
python main.py
```

This will start a Gradio server at http://127.0.0.1:7860, allowing us to chat to the scraped website and data store.

NOTE: we must both first scrape a site and persist a vector store in order for this to work.
