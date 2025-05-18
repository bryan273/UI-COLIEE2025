# UI-COLIEE2025: Task 4 – Legal Textual Entailment  

The Competition on Legal Information Extraction/Entailment (COLIEE) encourages
progress in automatic legal reasoning. We participated in **Task 4 – Legal Textual Entailment** and submitted two
official runs that favour minimal compute while still supporting voting and advanced reasoning:

| Run-ID | Idea in one line |
|--------|------------------|
| **XXRunLang** | Pick the Japanese language, ask Qwen-2-72B with three high-precision prompts, decide by majority vote |
| **XXRunCoT**  | Re-inspect hard cases from XXRunLang with dedicated CoT / ToT / GoT prompts, then vote |

The notebook is fully executable and reproduce the files we sent to the organisers.

--------------------------------------------------------------------------------
## 1 Results

(official scores released by the COLIEE organisers)

Note that \textbf{UIRunCoT} was excluded from the official table because, at the time of the competition, we employed a version of an LLM that was prohibited by COLIEE regulations.

| Run | Accuracy (%) | Data |
|-----|--------------|-----|
| UIRunCoT | 80.09 | Validation |
| UIRunLang | 82.19 | Test |
| UIRunFTune | 60.27 | Test |

--------------------------------------------------------------------------------
## 2 Data

Request the original material from the COLIEE committee or download the processed one from the google drive attached in the notebook. After unpacking keep the data in the root directory:

Each CSV row will have these main columns

`id, t1, t2, t1_japan, t2_japan, label`

* `t1` / `t2`   English article & hypothesis  
* `t1_japan` / `t2_japan`   Japanese originals  
* `label`   Y / N (train & dev only)

--------------------------------------------------------------------------------
## 3 Requirements

Hardware:

* UIRunLang — CPU
* UIRunCoT — CPU

Set your OpenRouter key:
OPENAI_API_KEY="<YOUR_OPENROUTER_KEY>"

4 How to reproduce

1. Put the CSV files into data/COLIEE2025/
2. Launch the notebook

Both notebooks checkpoint intermediate results so you can interrupt/resume
without losing finished generations.

--------------------------------------------------------------------------------

## 6 Citation
@inproceedings{UILegal2025,
  title     = {IRNLPUI at COLIEE 2025: Utilization of LLMs for Statute Law Retrieval and Legal Entailment Task},
  author    = {Bryan Tjandra, Made Swastika Nata Negara, Alfan Farizki Wicaksono},
  booktitle = {Proceedings of the COLIEE 2025 Workshop},
  year      = {2025}
}

--------------------------------------------------------------------------------

## 7 License
The code in this repository is released under the MIT License.
Weights of third-party models remain under their respective licenses.
