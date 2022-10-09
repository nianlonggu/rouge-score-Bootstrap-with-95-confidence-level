# rouge-score-Bootstrap-with-95-confidence-level
A code snippet for using the rouge-score bootstrapping sampling method to compute the confidence level of rouge scores. This is supported by the package rouge-score.

# Tested on rouge-score 0.1.2
# requiement: 
```bash
pip install rouge-score
```

# Python code for computing bootstraping rouge scores:
```python
from rouge_score.scoring import BootstrapAggregator
from rouge_score import rouge_scorer

scorer = rouge_scorer.RougeScorer(['rouge1', 'rougeL'])
aggregator = BootstrapAggregator()
aggregator.add_scores(scorer.score("one two three", "one two"))
aggregator.add_scores(scorer.score("one two five six", "seven eight"))
result = aggregator.aggregate()

print(result)

```
```
{'rouge1': AggregateScore(low=Score(precision=0.0, recall=0.0, fmeasure=0.0), mid=Score(precision=0.5, recall=0.3333333333333333, fmeasure=0.4), high=Score(precision=1.0, recall=0.6666666666666666, fmeasure=0.8)),
 'rougeL': AggregateScore(low=Score(precision=0.0, recall=0.0, fmeasure=0.0), mid=Score(precision=0.5, recall=0.3333333333333333, fmeasure=0.4), high=Score(precision=1.0, recall=0.6666666666666666, fmeasure=0.8))}
```

