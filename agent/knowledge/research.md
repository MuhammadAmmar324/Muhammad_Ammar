# Research: Med-GReF

**Title:** Med-GReF — Evidence-Guided Multimodal Fusion and Hallucination
Verification for Medical Vision-Language Reasoning.

**Ammar's role:** co-author / contributor.

**Status:** In-progress research project. A working paper has been drafted in
NeurIPS format but has NOT been submitted, published, or peer-reviewed. Do not say
it is "submitted to NeurIPS", "accepted", "published", or "under review".

## Summary

Vision-language models applied to medical imaging often produce fluent claims that
are not backed by the evidence in front of them. Med-GReF pairs frozen
vision-language backbones (BiomedCLIP, PubMedBERT) with quantitative radiomics
features, Grad-CAM saliency, an evidence-guided cross-attention fusion network,
and a dedicated natural-language-inference (NLI) verifier that scores whether a
model's stated conclusion is entailed by its own retrieved evidence.

Draft results on a held-out, article-grouped test split show accuracy improving
from 0.817 to 0.912 and ROC-AUC from near-chance (0.570) to 0.881, with undetected
hallucinations on constructed contradiction pairs cut roughly 2.4x. These are
unpublished, in-progress numbers.

The draft paper PDF is hosted on the lead author's site:
https://safwan2003.github.io/Safwan_Ali/assets/Med-GReF_Paper.pdf
