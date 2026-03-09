# Dialogue Breakdown Repair Corpus (DBRC)

- 準備中です．

本リポジトリでは、**対話破綻が発生した際にユーザがどのように反応し、どのような修復発話を期待するか**を分析するために構築した日本語対話コーパスを公開しています。

本データセットは以下の論文で発表予定です。

**Kazuya Tsubokura et al. (2026)**
*A Corpus for Personalized Dialogue Breakdown Repair in Japanese Open-Domain Conversations*
Proceedings of **LREC 2026**

---

# 概要

近年、大規模言語モデル（LLM）の進展により対話システムの応答精度は大きく向上しました。
しかし、依然として以下のような問題が発生することがあります。

* 誤情報を含む発話（hallucination）
* 文脈を無視した応答
* 常識に反する発話
* 話題の逸脱

このような問題は **対話破綻（dialogue breakdown）** と呼ばれ、ユーザに不快感を与えたり、困惑させる要因となります。

本コーパスは、対話破綻が発生した状況において

* システムの破綻した発話に対して、ユーザがどの程度破綻と感じるか（1:破綻ではない～10:破綻10段階） 
* システムの破綻した発話に対して、ユーザがどのような応答をするか
* ユーザがシステムにどのような修復発話を期待するか

を分析することを目的として構築されました。

---

# データセット概要

| 項目     | 内容    |
| ------ | ----- |
| 参加者数   | 57名   |
| 対話破綻類型 | 10種類  |
| 破綻パターン | 140個 |
| 修復事例数  | 3,990個 |
| 言語     | 日本語   |

対話破綻類型は，[先行研究 (東中 他; 2022)](https://www.jstage.jst.go.jp/article/jnlp/29/2/29_443/_article/-char/ja/)を参考に次の10種類を選定しました：誤情報，質問無視，期待無視，発話意図不明確，話題遷移エラー，情報不足，自己矛盾，相手の発話との矛盾，繰り返し，常識欠如

---

# データ形式

各データは以下の情報を含みます。

* 対話履歴（最後のシステム発話が対話破綻を引き起こしている）
* 対話破綻の類型
* 破綻度
* ユーザの反応発話
* ユーザが期待する修復発話

例：

```json
{
  "dialogue_history": [
    {"role": "user", "text": "今日は暑いね"},
    {"role": "system", "text": "今日は雪が降っています"}
  ],
  "breakdown_type": "misinformation",
  "severity": 8,
  "user_response": "いや、雪は降ってないよ",
  "expected_repair": "ごめんなさい、間違えました。今日はとても暑いですね。"
}
```

---

# 想定される研究用途

本データセットは以下の研究に利用できます。

* 対話システムのエラー分析
* 対話破綻を修復する発話の生成

---

# ライセンス

本データセットは **Creative Commons Attribution 4.0 International (CC BY 4.0)** の下で公開されています。

詳細は LICENSE ファイルをご確認ください。

---

# 引用

本データセットを使用する場合は、以下の論文を引用してください。

```bibtex
@inproceedings{tsubokura2026repair,
  title={A Corpus for Personalized Dialogue Breakdown Repair in Japanese Open-Domain Conversations},
  author={Tsubokura, Kazuya and Iribe, Yurie and Kitaoka, Norihide},
  booktitle={Proceedings of LREC},
  year={2026}
}
```

---

# 免責事項

本データセットは研究目的で公開されています。
データの利用によって生じたいかなる損害についても、著者は責任を負いません。

---

# 連絡先

坪倉 和哉
愛知県立大学
