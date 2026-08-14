# LangChain – Chat With Search

An AI agent that answers your questions by autonomously searching the web, Arxiv, and Wikipedia. Unlike a plain chatbot, this app uses a **tool-calling agent** — it decides on its own which tool(s) to use for each question, and you can watch its reasoning and actions unfold live in the chat.

## 🔗 Live Demo

**[Launch App](https://search-engine-khpl8hwpmd9mqgvwmocfkw.streamlit.app)**

> Enter your Groq API key in the sidebar and start chatting. Bring your own Groq key.

## ✨ Features

- **Web search** via DuckDuckGo for up-to-date, general information.
- **Arxiv search** for scientific papers and research.
- **Wikipedia search** for encyclopedic facts.
- **Autonomous tool selection** — the agent chooses which tool fits each question.
- **Live agent reasoning** — a Streamlit callback handler streams the agent's thoughts and actions as it works.
- **Chat interface** with conversation history kept in session state.

## 🔍 How It Works

This app is built around a LangChain **tool-calling agent**. Three tools are registered — DuckDuckGo web search, an Arxiv query tool, and a Wikipedia query tool. When you ask a question, the agent (powered by a Groq-hosted model) reasons about which tool is most appropriate, calls it, reads the result, and may call additional tools before composing its final answer. The `StreamlitCallbackHandler` surfaces each intermediate step in the UI, so you can see the agent think rather than just getting a black-box reply. The `AgentExecutor` runs this loop and handles parsing errors gracefully.

## 🛠️ Tech Stack

- [Streamlit](https://streamlit.io/) — chat UI and live agent trace
- [LangChain](https://www.langchain.com/) — tool-calling agent and executor
- [Groq](https://groq.com/) — fast LLM inference (`openai/gpt-oss-120b`)
- **Tools:** DuckDuckGo search, Arxiv, Wikipedia

## 🚀 Getting Started

### 1. Clone the repo

\`\`\`bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
\`\`\`

### 2. Install dependencies

\`\`\`bash
pip install -r requirements.txt
\`\`\`

If you don't have a \`requirements.txt\` yet, install the core packages:

\`\`\`bash
pip install streamlit langchain langchain-groq langchain-community "arxiv==2.1.3" wikipedia duckduckgo-search python-dotenv
\`\`\`

### 3. Run the app

\`\`\`bash
streamlit run search.py
\`\`\`

Then enter your Groq API key in the sidebar and ask away.

## 📝 Notes

- The Groq API key is entered in the app at runtime, so each visitor uses their own key.
- Get a free Groq API key at [console.groq.com](https://console.groq.com).
- DuckDuckGo occasionally rate-limits automated searches; if a search fails, try again in a moment.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
