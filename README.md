# PS 26 — AI-Powered LaTeX Diagram Generator

> Convert plain-English descriptions into publication-ready TikZ/LaTeX 
> diagrams using IBM Watson Studio and IBM Granite models.

---

## Overview

An intelligent agent built on IBM Watson Studio that automatically generates 
professional TikZ code for LaTeX documents from natural language descriptions. 
Researchers can describe a diagram in plain English, receive valid TikZ code, 
preview the rendered diagram instantly, and refine it iteratively — all without 
leaving IBM Watson Studio or writing a single line of LaTeX manually.

---

## Tech Stack

| Component         | Technology                              |
|-------------------|-----------------------------------------|
| Environment       | IBM Watson Studio (Jupyter Notebook)    |
| AI Model          | IBM Granite 8B Code Instruct            |
| Model Platform    | IBM watsonx.ai Runtime                  |
| SDK               | ibm-watsonx-ai (Python)                 |
| Rendering         | matplotlib + networkx                   |
| Language          | Python 3.12                             |

---

## Features

- Natural language → TikZ code generation
- Supports: flowcharts, trees, state machines, block diagrams,
  sequence diagrams, timelines, Venn diagrams
- Live diagram preview rendered inside the notebook
- Plain-English refinement (multi-turn)
- Color, style, and layout customization via natural language
- No LaTeX installation required
- Publication-ready output

---

## Setup

### 1. Prerequisites
- IBM Cloud account
- IBM Watson Studio project created
- watsonx.ai Runtime service associated with the project

### 2. Get Credentials
- **API Key**: IBM Cloud → Manage → Access (IAM) → API Keys → Create
- **Project ID**: Watson Studio project → Manage tab → Project ID

### 3. Open Watson Studio
- Create a new Jupyter Notebook (Python 3.12 runtime)
- Copy the cells from `tikz_generator.ipynb`

### 4. Install Dependencies
Run Cell 1:
```python
!pip install -q ibm-watsonx-ai matplotlib networkx Pillow
```

### 5. Add Credentials
In Cell 2, replace:
```python
api_key    = "YOUR_IBM_API_KEY"
PROJECT_ID = "YOUR_PROJECT_ID"
```

### 6. Run All Cells
- **Cell 2**: Setup and model loading
- **Cell 3**: Generate your first diagram
- **Cell 4**: Refine with plain English
- **Cell 5**: Try different diagram types

---

## Usage Examples

**Generate a flowchart:**
```python
current_code = generate_tikz(
    description  = "A flowchart: Source Code → Lexer → Parser → AST → Machine Code",
    diagram_type = "flowchart"
)
compile_and_show(current_code)
```

**Refine it:**
```python
current_code = refine_tikz(current_code, "Add blue color to the Lexer and Parser nodes")
compile_and_show(current_code)
```
.
**State machine:**
```python
current_code = generate_tikz(
    description  = "A state machine: Idle → Processing → Success or Error → Idle",
    diagram_type = "state machine"
)
compile_and_show(current_code)
```

---

## Project Structure
