# Human-Centric PDF Outline Extraction Engine

1. ## Project Overview
This project is a **Python-based document processing system** designed to automatically extract structured outlines from PDF files. It identifies titles, headings, and sub-headings and represents them in a clean, hierarchical JSON format.

The solution follows a **human-centric approach**, focusing on how people visually read documents rather than relying on heavy machine learning models.

---

2. ## Key Features
- Extracts document structure such as titles, H1, H2, and H3 headings
- Uses layout-aware heuristics based on font size, font weight, spacing, and text positioning
- Lightweight and fast execution, suitable for large and complex PDFs
- Fully offline and CPU-based processing
- Robust handling of edge cases and unstructured documents

---

3. ## Technical Approach
The engine analyzes PDF layout metadata to determine heading importance. Instead of treating text uniformly, it considers:
- Relative font sizes
- Boldness and styling
- Line spacing and visual grouping
- Common numbering and formatting patterns

This approach improves transparency, interpretability, and consistency across different document formats.

---

4. ## Technologies Used
- Python 3
- PyMuPDF (for PDF text and layout extraction)
- Standard Python libraries such as `re`, `json`, and `collections`

---

5. ## Output Format
The extracted outline is generated in a structured JSON format, making it easy to integrate with:
- Search systems
- Document analysis pipelines
- Content indexing and summarization tools

---

6. ## Learning & Outcome
Through this project, I gained hands-on experience in:
- Python-based document processing
- Designing rule-based intelligent systems
- Handling real-world unstructured data
- Building scalable and human-aligned software solutions

7.  **Build the Docker Image:**
    * Open your terminal or command prompt and navigate to the root directory of your project .
    * Execute the following command to build the Docker image for your solution:
        ```bash
        docker build --platform linux/amd64 -t pdf-outline-extractor:latest .
        ```
        *(This command names your Docker image `pdf-outline-extractor` with the tag `latest`. You can customize `pdf-outline-extractor` to any preferred image name for local use.)*

8.  **Run the Docker Container:**
    * **Prior to running:** You must edit the `process_pdfs.py` file. Locate the `target_pdf_to_process` variable and set its value to the specific PDF file you intend to process in this run (e.g., `target_pdf_to_process = "sample-data_sets/PDFs/file03.pdf"`). This script is designed to process one specified PDF at a time for localized testing.
    * Execute the Docker container using the following command. This command effectively maps your local input and output folders to the corresponding directories expected within the Docker container (`/app/input` and `/app/output`):
        ```bash
        docker run --rm -v "$(pwd)/sample-data_sets/PDFs:/app/sample-data_sets/PDFs" -v "$(pwd)/output:/app/output" --network none pdf-outline-extractor:latest
        ```
        *(**Note for Windows Users:** If you are using `cmd.exe`, replace `$(pwd)` with `%cd%`. If using PowerShell, use `${PWD}`. For example: `-v "%cd%/sample-data_sets/PDFs:/app/sample-data_sets/PDFs"`)*
        *(The `--rm` flag ensures the container is automatically removed after its execution is complete. The `--network none` flag is critical as it strictly prevents any internet access during runtime, adhering to hackathon constraints.)*

9.  **View Output:**
    * The generated JSON output file (e.g., `file03_output.json`) will be conveniently saved within your local `output/` directory, located at the root of your project.
