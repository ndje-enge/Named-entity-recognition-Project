# Named Entity Recognition (NER) with spaCy and CamemBERT

This work is part of a school project in collaboration with the CNAM (Conservatoire national des arts et métiers). The goal was to explore NER in historical texts allowing fast interpretation by historians. 

This work demonstrates and compares Named Entity Recognition (NER) in French and English using spaCy and CamemBERT models. It includes Wikipedia text extraction, entity detection, and entity comparison between models.

## Features

- **Wikipedia Text Extraction:**  
  Automatically fetches and cleans text from Wikipedia pages (English and French) using `requests` and `BeautifulSoup`.

- **NER with spaCy:**  
  Supports both English (`en_core_web_sm`,`en_core_web_lg`) and French (`fr_core_news_sm`, `fr_core_news_lg`) models.  
  Detects and displays entities, with a focus on extracting all PERSON entities.

- **NER with CamemBERT:**  
  Uses the HuggingFace `Jean-Baptiste/camembert-ner-with-dates` model for advanced French NER.

- **Entity Comparison:**  
  Provides code to compare and combine results from spaCy and CamemBERT.

## File Overview

- **SpacyWIKI.ipynb:**  
  - Fetches and cleans Wikipedia text in English and French.
  - Runs NER with various spaCy models.
  - Extracts and counts PERSON entities.

- **Spacy combined with Camembert.ipynb:**  
  - Runs spaCy and CamemBERT NER on a local text file (`dataset.txt`).
  - Compares and merges entity results from both models.

- **dataset.txt:**  
  - Local text file used for NER experiments.

## Installation

Install the required dependencies:

```bash
pip install spacy transformers torch sentencepiece beautifulsoup4 requests protobuf==3.20.3
python -m spacy download en_core_web_sm
python -m spacy download en_core_web_lg
python -m spacy download fr_core_news_sm
python -m spacy download fr_core_news_lg
```

## Usage

1. **Wikipedia NER (English & French):**  
   Open `SpacyWIKI.ipynb` and run the cells to:
   - Download and clean Wikipedia text.
   - Run NER with spaCy.
   - Extract and count PERSON entities.

2. **NER on Local Text (French):**  
   Place your text in `dataset.txt`.  
   Open `Spacy combined with Camembert.ipynb` to:
   - Run spaCy and CamemBERT NER.
   - Compare and merge entity results.

## Example: Extracting PERSON Entities with spaCy

```python
import spacy
nlp = spacy.load("en_core_web_sm")
doc = nlp(text_without_brackets)
all_person = [ent.text for ent in doc.ents if ent.label_ == 'PERSON']
print("Person Names:", all_person)
print("Count:", len(all_person))
```

## Notes

- Designed for use in Jupyter or VS Code notebooks.
- CamemBERT model is loaded from HuggingFace: `Jean-Baptiste/camembert-ner-with-dates`.
- For entity visualization, use `spacy.displacy.render`.
