# gnn-indaba-2026
Materials for "Graph Neural Networks: Foundations and Applications for Real-World Networks," a tutorial at Deep Learning Indaba 2026.

## Notebooks

- [Live demo notebook](https://colab.research.google.com/github/Whizz-tamie/gnn-indaba-2026/blob/main/notebooks/GNN_Tutorial_Live.ipynb)
- [Take-home notebook](https://colab.research.google.com/github/Whizz-tamie/gnn-indaba-2026/blob/main/notebooks/GNN_Tutorial_TakeHome.ipynb)

## Slides

- [Tutorial slides](slides/DLI2026_GNNs_slidedeck.pdf)

## Dataset

The tutorial uses the MoMTSim synthetic mobile money transaction dataset from
Mendeley Data:

https://data.mendeley.com/datasets/zhj366m53p/2

The raw file, `synthetic_mobile_money_transaction_dataset.csv`, has 1,720,181
transactions and is about 149 MB. The raw file is not tracked in git. The
tutorial notebooks use a smaller prepared CSV so that setup remains fast and
reproducible.

The prepared sample is generated with `prepare_data.py`. The script keeps
simulation steps 0-143, corresponding to 144 hourly steps. The current source
file already contains this range, but the explicit filter keeps the preparation
logic stable if a longer MoMTSim export is used.

The preparation procedure:

- Select transactions from the 3,000 most active initiator accounts.
- Cap the sample at 50,000 transactions, producing a CSV of roughly 4-5 MB.
- Preserve the fraud rate of the selected active-account subset when sampling
  down to the cap.
- Store `initiator` and `recipient` as strings because they are identifiers,
  not numeric quantities.

This sample is designed for a compact GNN teaching graph. It preserves useful
repeated account activity and the approximate fraud balance, but it should not
be interpreted as a faithful miniature of the full temporal simulation. Random
edge sampling can break complete account histories and balance continuity.

The live-demo notebook keeps dataset discussion brief and focuses on graph
construction and model flow. The take-home notebook includes additional context
on data provenance, sampling decisions, and limitations of the prepared sample.
