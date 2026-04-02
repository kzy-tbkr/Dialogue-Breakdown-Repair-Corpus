# Dialogue Breakdown Repair Corpus (DBRC)

This repository releases the **Japanese Dialogue Breakdown Repair Corpus (DBRC)**, which was constructed to analyze **how users react to dialogue breakdowns in open-domain chat-oriented dialogue systems and what kinds of repair utterances they expect from the system**.

![Overview of this corpus](img/overview.png)

The dataset is available here:

[data/DBRC_dataset_v1.0.jsonl](data/DBRC_dataset_v1.0.jsonl)

This dataset is presented in the following paper:

**Kazuya Tsubokura et al. (2026)**
*A Corpus for Personalized Dialogue Breakdown Repair in Japanese Open-Domain Conversations*
Proceedings of **LREC 2026**

---

## Overview

Recent advances in Large Language Models (LLMs) have significantly improved the response quality of dialogue systems.  
However, dialogue systems still occasionally produce problematic responses, such as:

- utterances containing incorrect information (**hallucinations**)
- responses that ignore the dialogue context
- utterances inconsistent with common sense
- topic shifts that break conversational flow

These issues are commonly referred to as **dialogue breakdowns**, which may confuse or frustrate users.

This corpus was constructed to analyze the following aspects when a dialogue breakdown occurs:

- how strongly users perceive the system utterance as a breakdown (Q1)  
  (**1 = not a breakdown, 10 = severe breakdown**)
- how users respond to the broken system utterance (Q2)
- what kind of repair utterance users expect from the system (Q3)

## Dataset Statistics

| Item | Value |
|---|---|
| Number of participants | 57 |
| Breakdown types | 10 |
| Breakdown patterns | 140 (10 types × 14 patterns each) |
| Repair instances | 3,990 (57 participants × 70 responses each) |
| Language | Japanese |

The 10 dialogue breakdown types were selected based on the taxonomy proposed in the prior work by Higashinaka et al. (2022).

The selected types are:

- Wrong information
- Ignore question
- Ignore expectation
- Unclear utterance intention
- Topic transition error
- Lack of information
- Self-contradiction
- Contradiction with the user's utterance
- Repetition
- Lack of common sense

## Data Format

Each data instance contains the following fields:

- `question_id`: breakdown pattern ID
- `dialogue_history`: dialogue history  
  (the last system utterance causes the dialogue breakdown)
- `breakdown_type`: type of dialogue breakdown
- `breakdown_reason`: reason why the utterance is considered a breakdown
- `severity`: perceived breakdown severity
- `user_response`: user’s response utterance
- `expected_repair`: repair utterance expected by the user

The dialogue history consists of **2 to 4 utterances**.  
If an utterance does not exist, `NaN` is stored.

### Example

```json
{
  "question_id": 1,
  "dialogue_history": [
    {"role": "user", "text": "駅前に新しくできたケーキ屋さん知ってますか？\n"},
    {"role": "system", "text": "はい、知ってますよ。おいしそうですよね、気になっています。\n"},
    {"role": "user", "text": "そうなんですね！美味しそうなケーキありましたか？\n"},
    {"role": "system", "text": "ありました。"}
  ],
  "breakdown_type": "期待無視",
  "breakdown_reason": "美味しそうなケーキを答えることが期待されている",
  "severity": 1,
  "user_response": "そのケーキ教えて",
  "expected_repair": "イチゴのショートケーキです"}
}
```

```json
{
  "question_id": 29,
  "dialogue_history": [
    {"role": "user", "text": "日本の首都は東京です。\n"},
    {"role": "system", "text": "そうですね、東京はユニバーサルスタジオジャパンも有名ですよね。"},
    {"role": "user", "text": NaN},
    {"role": "system", "text": NaN}
  ],
  "breakdown_type": "誤情報",
  "breakdown_reason": "ユニバーサルスタジオジャパンは大阪にあるため，明らかに事実とは異なる内容が含まれている",
  "severity": 10,
  "user_response": "ユニバは大阪ですよ。",
  "expected_repair": "うっかりしてました。"
}


```

## Potential Research Applications

This dataset can be used for research on:

- error analysis of dialogue systems
- generation of repair utterances for dialogue breakdown recovery
- personalized dialogue repair strategies
- dialogue breakdown severity prediction

## License

This dataset is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

## Citation

If you use this dataset, please cite:

```bibtex
@inproceedings{tsubokura2026repair,
  title={A Corpus for Personalized Dialogue Breakdown Repair in Japanese Open-Domain Conversations},
  author={Tsubokura, Kazuya and Iribe, Yurie and Kitaoka, Norihide},
  booktitle={Language Resources and Evaluation Conference (LREC)},
  year={2026}
}
```

## Disclaimer

This dataset is released for research purposes only.

The authors are not responsible for any damages resulting from the use of this dataset.

## Contact

For questions about the dataset, please contact:

**Kazuya Tsubokura**

Aichi Prefectural University

Email: tsubokura [at] ist.aichi-pu.ac.jp

(Please replace `[at]` with `@`.)
