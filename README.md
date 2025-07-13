# Smart Assistant for Research Summarization

## 📚 Project Overview

This project develops a simple AI assistant focused on **text and document summarization**. It allows users to input text directly or upload PDF/TXT documents, and then generates a concise summary using the `txtai` library. This serves as a foundational step towards building a more comprehensive document-aware AI assistant.

**Objective:** To provide a basic utility for quickly summarizing textual content from various sources.

## ✨ Features

This assistant currently offers the following functionalities:

  * **Text Summarization:** Users can paste any text directly into the application to get a summarized version.
  * **Document Summarization (PDF/TXT):** Supports uploading documents in `PDF` or `TXT` format. The application extracts text from the first page of PDF files and summarizes it.
  * **Concise Auto-Summary:** Upon document upload and processing, a summary of the extracted text is displayed.
  * **Intuitive Web Interface:** A clean, user-friendly local web application built with Streamlit.

## 🚀 Getting Started

Follow these instructions to set up and run the Document Summarization Assistant on your local machine.

### Prerequisites

Before you begin, ensure you have the following installed:

  * Python (version 3.8 or higher recommended)
  * `pip` (Python package installer)

### Installation

1.  **Clone the repository (if you haven't already):**

    ```bash
    git clone https://github.com/YOUR_USERNAME/document-summarization-assistant.git
    cd document-summarization-assistant
    ```

    *(Replace `YOUR_USERNAME` with your GitHub username and `document-summarization-assistant` with your repository name.)*

2.  **Create a virtual environment (recommended):**

    ```bash
    python -m venv venv
    # On Windows
    .\venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate
    ```

3.  **Install dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

    **`requirements.txt` content:**

    ```
    txtai[all]
    streamlit
    PyPDF2
    ```

### Running the Application

1.  **Start the application:**

    ```bash
    streamlit run app.py
    ```

2.  **Access the application:**
    Open your web browser and navigate to `http://localhost:8501` (or the specific address displayed in your terminal).

## 🏗️ Application Architecture & Reasoning Flow

The application follows a straightforward client-server architecture, with Streamlit handling both the frontend and the basic backend logic.

### High-Level Architecture

```
+-------------------+       +-------------------+
|     User Interface|----->|   Streamlit App   |
|   (Web Browser)   |      |   (app.py)        |
+-------------------+       +-------------------+
        |                            |
        |                            |
        V                            V
+-------------------+       +-------------------+
| Document Upload   |----->| PyPDF2 / txtai    |
| (PDF/TXT)         |      | (Text Extraction, |
+-------------------+       | Summarization)    |
```

### Component Breakdown and Reasoning Flow

1.  **Frontend (User Interface):**

      * **Purpose:** Provides a simple web interface for users to interact. It allows text input, file uploads, and displays the summarization results.
      * **Technology:** `Streamlit`.
      * **Flow:**
          * Users select between "Summarize Text" and "Summarize Document" modes via a sidebar.
          * In "Summarize Text" mode, a text area allows direct input.
          * In "Summarize Document" mode, a file uploader accepts PDF or TXT files.
          * Upon clicking the "Summarize" button, the input (text or file) is processed.

2.  **Backend Logic (within `app.py`):**

      * **Purpose:** Handles text extraction from documents and performs the summarization.
      * **Technology:** `PyPDF2` for PDF text extraction, `txtai` for summarization.
      * **Flow:**
          * **PDF/TXT Handling:**
              * For PDF files, `PyPDF2` is used to read the first page and extract its text content.
              * For TXT files, the content is read directly (though the current code saves PDFs to `doc_file.pdf` and then reads from it, and doesn't explicitly handle TXT file content reading beyond the `st.file_uploader` type hint).
          * **Summarization:** The extracted text (or direct text input) is passed to the `txtai.pipeline.Summary()` instance. This `txtai` model then generates a concise summary.
          * **Display:** The original input/extracted text and the generated summary are displayed side-by-side in the Streamlit interface.

## 🛠️ Technologies Used

  * **Frontend & Backend Framework:** `Streamlit`
  * **Text Summarization:** `txtai`
  * **PDF Parsing:** `PyPDF2`

## 🤝 Contributing

Contributions are welcome\! If you have suggestions for improvements or new features for this summarization tool, or want to contribute to expanding it into the full Document-Aware AI Assistant, please open an issue or submit a pull request.

## 📄 License

This project is licensed under the [MIT License](https://www.google.com/search?q=LICENSE). *(Create a `LICENSE` file in your repository)*

-----
