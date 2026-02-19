# TranslationPipeline

A robust translating pipeline designed for multi-file support and integration with multiple translation sources, enabling users to efficiently process and translate large datasets or documents across various formats and languages into a JSON in the target language.

## Funcionalities
- Flexible Translation Methods: Easily switch between translation APIs and models.
- Extensible: Add new file formats or translation methods with minimal effort.
- JSON Output: Consolidate translations into a structured JSON for easy integration.

### Format Support:
- JSON
- JSONL
- XML
- TML
- CSV
- Hugging Face Datasets

### Translation Methods:
- Deep Translator (supports Google, Microsoft, and other APIs)
- Models (Via transformers Pipeline)

## Requirements
- Python 3.10+
- Dependencies listed in `requirements.txt`
- Internet access for Deep Translator or Hugging Face models

## Installation

1. Clone Repository 
```bash
git clone https://github.com/LIAAD/D-UniTS-Translation-Pipeline.git
```

2. Create virtual environment
```bash
python3 -m venv venv
```

3. Activate virtual environment
```bash
source venv/bin/activate   # Linux/macOS
# venv\Scripts\activate    # Windows
```

4. Install dependencies
```bash
pip install -r requirements.txt
```

5. Create config.json inside config/
```bash
touch config/config.json 
```

6. Adapt config.json following config_example.json. Example:
```
{       
        "name": "bigbench",
        "method": "model",
        "dataset": "tasksource/bigbench",
        "version": "movie_recommendation",
        "backup_interval": 5,
        "columns2translate": ["inputs", "targets", "multiple_choice_targets"],
        "model": "rhaymison/opus-en-to-pt-translator",
        "max_tokens":400,
        "col_id":"idx",
        "reader":"hugging_face",
        "source_language": "en",
        "target_language": "pt"   
}
```

7. Run the pipeline
```bash
python3 main.py
```

## Contributors

| Name              | Role      | Contact                                                     |
|-------------------|-----------|-------------------------------------------------------------|
| **José Soares**   | Developer | [jose.p.soares@inesctec.pt](mailto:jose.p.soares@inesctec.pt)     |
| **Nuno Guimarães** | Advisor   | |

## License

MIT License

Copyright (c) 2025 INESC TEC

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

