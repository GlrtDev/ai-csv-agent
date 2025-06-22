# AI CSV Data Analyst 📊

-----

This application allows you to upload CSV files, ask natural language questions, and receive AI-generated analyses.
Its using small 1Bit BitNet LLM so it can be run on almost all consumer PCs.

## Technologies Used 🛠️

Both frontend and backend are containerized using docker.

### Frontend

  * **React**
  * **Vite**
  * **TypeScript**

The frontend source code can be found here: [ai-csv-agent-frontend](https://github.com/GlrtDev/ai-csv-agent-frontend)

### Backend

  * **Python**
  * **FastAPI**
  * **BitNet 1Bit LLM:** A 1-bit [LLM developed by Microsoft](https://github.com/microsoft/BitNet), serving as the core AI agent.

The backend source code can be found here: [ai-csv-agent-backend](https://github.com/GlrtDev/ai-csv-agent-backend)

## Installation and Setup 🚀

To get this project up and running on your local machine, follow these steps:

1.  **Clone the repository with submodules:**

    ```bash
    git clone --recurse-submodules https://github.com/GlrtDev/ai-csv-agent-app.git
    cd ai-csv-agent-app
    ```

2.  **Address `llama.cpp` build issue (if encountered):**
    If you experience build errors related to `std::chrono` in `log.cpp` when compiling `llama.cpp` (a dependency of BitNet), you'll need to apply a specific commit.

    Navigate into the `ai-csv-agent-backend/BitNet/3rdparty/llama.cpp` directory (or wherever `llama.cpp` is located after cloning submodules) and apply the changes from this commit:
    [https://github.com/tinglou/llama.cpp/commit/4e3db1e3d78cc1bcd22bcb3af54bd2a4628dd323](https://github.com/tinglou/llama.cpp/commit/4e3db1e3d78cc1bcd22bcb3af54bd2a4628dd323)

    You can often do this by:

    ```bash
    cd path/to/ai-csv-agent-backend/BitNet/3rdparty/llama.cpp # Adjust path if needed
    git cherry-pick 4e3db1e3d78cc1bcd22bcb3af54bd2a4628dd323
    ```
    *Note: Ensure you are in the correct `llama.cpp` directory before running the `git cherry-pick` command.*

    if this failes then you would need to edit those files manually.

3.  **Run with Docker Compose:**
    Launch the entire application using Docker Compose. Make sure you have Docker installed and running on your system.

    ```bash
    docker compose up
    ```

## Usage

After successfully running `docker compose up`, the services will be accessible at the following addresses:

  * **Frontend:** `http://localhost:3000`
  * **Backend:** `http://localhost:8000`


## Future plans

This project is an working draft, only binds separate parts together and have been started as a side project. There are multiple things to finish:
 - end tokens in LLM
 - streaming LLM output instead of waiting for call to finish
 - limit incomming traffic (secure against DDoS)
 - data processing agreements for users
 - allow multi datasource plots
 - and much more...
