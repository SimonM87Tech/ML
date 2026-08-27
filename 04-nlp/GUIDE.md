# NLP (text)

Models that understand language. The field LLMs came from — which means the key advisory question here is *build vs prompt*.

## Keywords decoded

- **Tokenization** — splitting text into pieces (subwords) a model can number. "unbelievable" → "un", "believ", "able".
- **Embedding** — a vector (list of numbers) representing a word/sentence/document such that similar meanings land near each other. The foundation of search, clustering, and RAG.
- **Transformer** — the architecture behind everything modern (BERT, GPT, Claude). Its core trick, **attention**, lets every word look at every other word to build context.
- **BERT-style vs GPT-style** — encoders (BERT): read whole text, best for classification/extraction; small, cheap, fine-tunable on a laptop. Decoders (GPT): generate text. Classifying 100k support tickets? Fine-tuned small BERT beats an LLM API on cost and latency.
- **Fine-tuning** — continuing training of a pretrained model on your labeled examples. Same idea as transfer learning in vision.
- **Zero-shot / few-shot** — solving a task via prompting an LLM with no / a handful of examples, no training at all.
- **RAG (retrieval-augmented generation)** — embed documents → store in a vector DB → retrieve relevant chunks → hand to an LLM to answer. You've already built this (ai-expert/Gentrix); it's NLP plumbing, not model training.
- **Hugging Face** — the ecosystem: model hub + `transformers` library. `pip install transformers`, load a pretrained model in 3 lines. The PyTorch of NLP.
- **NER (named entity recognition)** — extracting names/dates/amounts from text. **Sentiment analysis** — classifying tone. Both classic fine-tuning targets.

## The decision ladder (advisor gold)

For any text task, try in order — stop at the first that meets quality/cost/latency needs:
1. Prompt an LLM API (hours of work)
2. Few-shot prompt with examples (a day)
3. Fine-tune a small open model (a week, needs ~500+ labeled examples)
4. Train from scratch (almost never justified)

Most consultants only know step 1. Knowing when step 3 wins — high volume, low latency, privacy constraints, or cost at scale — is a differentiator.

## What to master

Fine-tune one small transformer for classification (Mission 03), compute embeddings and use them for similarity, and articulate the decision ladder with real cost numbers.

## Advisor lens

Clients conflate "AI" with "ChatGPT." Your value: mapping their problem onto the ladder above and being honest about where it lands. A fine-tuned DistilBERT running on their own server for $0 per request is sometimes the answer the LLM vendors won't give them.
