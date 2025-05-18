# UI-COLIEE 2025 – Task 4: Legal Textual Entailment  
Bryan Tjandra • Made Swastika Nata Negara • Alfan Farizki Wicaksono  
(Indonesia Research NLP & Universitas Indonesia)

The Competition on Legal Information Extraction/Entailment (COLIEE) fosters
research in automatic legal reasoning.  
We participated in **Task 4 – Legal Textual Entailment** and submitted two runs
that deliberately rely on *prompt engineering* instead of fine-tuning,
so that anyone can reproduce them on commodity hardware.

| Run-ID        | One-line description                          |
| --------------| --------------------------------------------- |
| **UIRunLang** | Ask *Qwen-2-72B-Instruct* three concise prompts in Japanese and decide by majority vote |
| **UIRunCoT**  | Re-evaluate the hard cases from UIRunLang with specialised CoT / ToT / GoT prompts, then vote |

Both runs are self-contained; intermediate generations are checkpointed so
that you can stop and resume at any time.

---

## 2. Official results (released by the organisers)

| Run-ID      | Accuracy (%) | Split  |
| ----------- | ------------ | ------ |
| XXRunLang   | 82.19        | Test   |
| XXRunCoT¹   | 80.09        | Dev    |
| XXRunFTune² | 60.27        | Test   |

¹ Not ranked officially because the model version was no longer on the COLIEE white-list when the leaderboard froze.  
² Internal ablation study (small fine-tune on Qwen 2-7B).

---

## 3. Data

The organisers provide the raw XML/HTML.  
We publish the *processed* CSV used in our code here:  

data/COLIEE_dataset_H30-R02.csv

Columns:

* `id`                 – numerical id  
* `t1`, `t2`           – English statute & hypothesis  
* `t1_japan`, `t2_japan` – Japanese originals  
* `label`              – ground-truth (Y/N) where available  

---

## 4. Requirements

* Python ≥ 3.9  
* `pip install -r requirements.txt` (see file)  
* Hardware: CPU is sufficient (GPU reduces latency).  
* Environment variable:  

```
export OPENAI_API_KEY="<YOUR_OPENROUTER_KEY>
```


---

## 5. How to reproduce

1. Clone
```
git clone https://github.com/<you>/UI-COLIEE2025.git
cd UI-COLIEE2025
```

2. Put CSV into ./data
```
cp /path/to/COLIEE_dataset_H30-R02.csv data/
```

3. Launch notebook
```
jupyter lab
```

# open notebooks/XXRunLang.ipynb or XXRunCoT.ipynb and Run-All
Both notebooks save intermediate results to evaluated_results.csv
(or *_CoT.csv) so you can safely interrupt and resume.

---

## 6. Citation
```
@inproceedings{UILegal2025,
  title     = {IRNLPUI at COLIEE 2025: Utilisation of Large Language Models for Statute-Law Retrieval and Legal Entailment},
  author    = {Bryan Tjandra and Made Swastika Nata Negara and Alfan Farizki Wicaksono},
  booktitle = {Proceedings of the COLIEE 2025 Workshop},
  year      = {2025}
}
```

---

## 7. License
Code: MIT
Third-party model weights: subject to their respective licenses.
