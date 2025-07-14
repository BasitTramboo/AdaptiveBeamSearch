# Adaptive Beam Search: Enhancing Sequence Prediction with Delayed Pruning

## Overview
This repository contains the implementation and documentation for **Adaptive Beam Search with Delayed Pruning**, a novel modification to the classic beam search algorithm aimed at improving sequence generation tasks such as machine translation and text generation. By introducing a prediction window to delay pruning decisions, this method allows initially weak candidate sequences additional time to evolve, leading to higher-quality outputs. The project evaluates the approach on both custom-trained and pre-trained language models (DistilGPT, GPT-2, GPT-2 Medium) using metrics like SacreBLEU, ROUGE-L, BERTScore, and MAUVE.

## Features
- **Adaptive Beam Search Algorithm**: Extends standard beam search by deferring pruning decisions for a fixed prediction window (`W`), allowing better-informed sequence selection.
- **Custom Model**: A lightweight LSTM-based encoder-decoder model trained on the WMT14 German-English dataset for translation tasks.
- **Pre-trained Model Integration**: Evaluates the algorithm on pre-trained models (DistilGPT, GPT-2, GPT-2 Medium) using the WikiText-103 dataset.
- **Comprehensive Evaluation**: Measures performance using SacreBLEU, ROUGE-L, BERTScore, and MAUVE metrics, with experiments analyzing the impact of varying window sizes (`W=1` to `W=4`).

## Results
The proposed Adaptive Beam Search with Delayed Pruning demonstrates consistent improvements over standard beam search:
- **Custom Model**: Achieves a SacreBLEU score of 0.67 compared to 0.66 for standard beam search on the WMT14 dataset.
- **Pre-trained Models**: Shows significant gains in MAUVE scores (e.g., 4% improvement for GPT-2 Medium) and competitive performance in BERTScore (~80% accuracy).
- **Optimal Window Size**: Window sizes of `W=2` (custom model) and `W=3` (pre-trained models) provide the best trade-off between quality and computational efficiency.


## Limitations
- **Computational Overhead**: Larger window sizes (`W>3`) increase memory and inference time, with diminishing returns in quality.
- **Task-Specific Performance**: The method excels in tasks requiring contextual coherence (e.g., story generation) but shows marginal gains in strict token-matching tasks (e.g., translation evaluated by SacreBLEU).
- **Rank Instability**: Retaining low-ranked beams for longer may introduce noise, requiring careful tuning of `W`.


## Future Work
- Explore adaptive window sizing based on task or data characteristics.
- Extend the method to non-autoregressive models or multimodal tasks (e.g., image captioning).
- Optimize computational efficiency for larger window sizes using batch decoding or GPU parallelism.

## Contributors
- **Basit Ali Tramboo**
- **Meet Maratha**