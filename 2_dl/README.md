# Deep Learning

[← Back to main README](../README.md)

## 📖 Book Index — Part 2: Deep Learning

**Chapters:** [1. Neural network basics](#chapter-1-neural-network-basics) · [2. Framework fundamentals (PyTorch, TensorFlow / Keras)](#chapter-2-framework-fundamentals-pytorch-tensorflow--keras) · [3. Optimization & regularization](#chapter-3-optimization--regularization) · [4. CNNs (Convolutional Neural Networks)](#chapter-4-cnns-convolutional-neural-networks) · [5. Transfer learning](#chapter-5-transfer-learning) · [6. Computer Vision](#chapter-6-computer-vision) · [7. RNNs, LSTMs, GRUs](#chapter-7-rnns-lstms-grus) · [8. Attention & Transformers](#chapter-8-attention--transformers) · [9. Project: train & deploy a model](#chapter-9-project-train--deploy-a-model)

### Chapter 1: Neural network basics

🟢 Core · 📝 Notes coming

- **1.1** Neuron / perceptron
- **1.2** Activation functions: sigmoid, tanh, ReLU, softmax
- **1.3** Layers & the multi-layer perceptron (MLP)
- **1.4** Forward pass & loss
- **1.5** Backpropagation & the chain rule

**🔑 Key terms:** neuron, weight, bias, activation, forward pass, backpropagation, epoch, batch  
**🎯 You'll learn:** What a neural network computes and how it learns  
**🛠️ You can build:** An MLP from scratch in NumPy that classifies handwritten digits

### Chapter 2: Framework fundamentals (PyTorch, TensorFlow / Keras)

🟢 Core · 📝 Notes coming

- **2.1** Tensors & GPUs
- **2.2** Autograd
- **2.3** Building models: nn.Module / Keras layers
- **2.4** Dataset & DataLoader
- **2.5** The training loop
- **2.6** Saving & loading models

**🔑 Key terms:** tensor, device, autograd, module, optimizer, DataLoader, checkpoint  
**🎯 You'll learn:** Build and train networks with real frameworks  
**🛠️ You can build:** The same digit classifier in PyTorch and in Keras

### Chapter 3: Optimization & regularization

🟢 Core · 📝 Notes coming

- **3.1** SGD, momentum, Adam
- **3.2** Learning-rate schedules
- **3.3** Weight initialization
- **3.4** Dropout & weight decay
- **3.5** Batch normalization
- **3.6** Early stopping

**🔑 Key terms:** learning rate, momentum, Adam, scheduler, vanishing gradient, dropout, batch norm  
**🎯 You'll learn:** Make training faster, more stable and less prone to overfitting  
**🛠️ You can build:** Experiments comparing optimizers, with training curves

### Chapter 4: CNNs (Convolutional Neural Networks)

🟢 Core · [📄 Read the notes](#4-cnns-convolutional-neural-networks)

- **4.1** Convolution, filters & feature maps
- **4.2** Stride, padding & pooling
- **4.3** Building a CNN
- **4.4** Landmark architectures: LeNet → ResNet → ConvNeXt
- **4.5** Data augmentation

**🔑 Key terms:** kernel / filter, feature map, stride, padding, pooling, receptive field, skip connection  
**🎯 You'll learn:** How networks see images  
**🛠️ You can build:** A CIFAR-10 image classifier

### Chapter 5: Transfer learning

⚪ Later · 📝 Notes coming

- **5.1** Pretrained models
- **5.2** Feature extraction vs. fine-tuning
- **5.3** Freezing layers
- **5.4** Vision Transformers (ViT)

**🔑 Key terms:** pretrained, backbone, head, freeze, fine-tune  
**🎯 You'll learn:** Get strong results with little data by reusing big models  
**🛠️ You can build:** A custom image classifier (e.g. plant diseases) from a few hundred images

### Chapter 6: Computer Vision

⚪ Later · [📄 Read the notes](#6-computer-vision)

- **6.1** Image classification
- **6.2** Object detection
- **6.3** Segmentation
- **6.4** OCR
- **6.5** Image–text models (CLIP)

**🔑 Key terms:** bounding box, IoU, NMS, mAP, mask, anchor  
**🎯 You'll learn:** Go beyond 'what' to 'where' in images and video  
**🛠️ You can build:** A webcam object detector and a receipt text extractor

### Chapter 7: RNNs, LSTMs, GRUs

🟢 Core · [📄 Read the notes](#7-rnns-lstms-grus)

- **7.1** Sequences & the hidden state
- **7.2** Vanishing gradients
- **7.3** LSTM & GRU gates
- **7.4** Bidirectional RNNs & seq2seq
- **7.5** Why Transformers replaced them

**🔑 Key terms:** time step, hidden state, gate, cell state, seq2seq, teacher forcing  
**🎯 You'll learn:** How networks handle ordered data like text and time series  
**🛠️ You can build:** A character-level text generator and a sentiment classifier

### Chapter 8: Attention & Transformers

🟢 Core · [📄 Read the notes](#8-attention--transformers)

- **8.1** Why attention?
- **8.2** Self-attention: Query, Key, Value
- **8.3** Multi-head attention
- **8.4** Positional encoding
- **8.5** The Transformer block
- **8.6** Encoder, decoder & encoder–decoder families

**🔑 Key terms:** attention, query, key, value, head, causal mask, positional encoding, residual connection, LayerNorm  
**🎯 You'll learn:** The architecture behind every modern LLM  
**🛠️ You can build:** A Transformer block from scratch, and a BERT text classifier

### Chapter 9: Project: train & deploy a model

⚪ Later · 📝 Notes coming

- **9.1** Pick a vision or NLP task
- **9.2** Train with experiment tracking
- **9.3** Export & serve the model

**🔑 Key terms:** experiment tracking, ONNX, inference  
**🎯 You'll learn:** Take a model from notebook to something people can use  
**🛠️ You can build:** An image-classifier web demo

Legend: 🟢 Core = study now · ⚪ Later = after the core ([Core Path](../README.md#core-path))

---

## 4. CNNs (Convolutional Neural Networks)

Networks built for grid-shaped data such as images. Small filters slide over the input and learn local patterns: edges first, then textures and shapes, then whole objects.

**Prerequisites:** neural network basics (1), a framework (2), optimization & regularization (3).

**In this section:** [Core building blocks](#core-building-blocks) · [Typical shape flow](#typical-shape-flow) · [Landmark architectures](#landmark-architectures) · [Hands-On: CNNs](#hands-on-cnns)

### Core building blocks

| Block | What it does |
|---|---|
| **Convolution** | A learned filter slides across the image and produces a feature map |
| **Stride & padding** | Control how far the filter moves and whether the output keeps its size |
| **Activation (ReLU)** | Adds non-linearity |
| **Pooling (max / average)** | Downsamples feature maps and adds some translation invariance |
| **Batch normalization** | Stabilizes and speeds up training |
| **Fully connected head** | Turns the final features into class scores |

### Typical shape flow

```
Image (3×32×32) → [Conv → ReLU → Pool] × N → Flatten → FC → Softmax → class
```

### Landmark architectures

| Model | Year | Key idea |
|---|---|---|
| **LeNet-5** | 1998 | First practical CNN (handwritten digits) |
| **AlexNet** | 2012 | Deep CNN on GPUs, ReLU, dropout; won ImageNet |
| **VGG** | 2014 | Very deep stacks of small 3×3 convolutions |
| **GoogLeNet / Inception** | 2014 | Parallel filters of different sizes |
| **ResNet** | 2015 | Skip connections make 100+ layer networks trainable |
| **MobileNet / EfficientNet** | 2017–19 | Accurate models small enough for phones |
| **ConvNeXt** | 2022 | Modernized CNN that competes with Vision Transformers |

### Hands-On: CNNs

| # | Exercise | Tools |
|---|---|---|
| 4.1 | Implement a 2D convolution from scratch | NumPy |
| 4.2 | Train a small CNN on MNIST / Fashion-MNIST | PyTorch, Keras |
| 4.3 | Classify CIFAR-10 with data augmentation | PyTorch, torchvision |
| 4.4 | Build a mini-ResNet with skip connections | PyTorch |
| 4.5 | Visualize filters and feature maps, plus a Grad-CAM heatmap | PyTorch, Captum |

---

## 6. Computer Vision

Using deep learning to understand images and video, going beyond "what is in this image" to "where is it" and "which pixels belong to it".

**Prerequisites:** CNNs (4), transfer learning (5).

**In this section:** [Core vision tasks](#core-vision-tasks) · [Key vision concepts](#key-vision-concepts) · [Hands-On: Computer Vision](#hands-on-computer-vision)

### Core vision tasks

| Task | Output | Popular models |
|---|---|---|
| **Image classification** | One label per image | ResNet, EfficientNet, ViT |
| **Object detection** | Boxes + labels | YOLO, Faster R-CNN, DETR |
| **Semantic segmentation** | A class for every pixel | U-Net, DeepLab |
| **Instance segmentation** | A mask for each separate object | Mask R-CNN, YOLO-seg |
| **Promptable segmentation** | A mask for whatever you click or describe | SAM (Segment Anything) |
| **Pose estimation** | Body keypoints | OpenPose, YOLO-pose |
| **OCR** | Text found in an image | Tesseract, EasyOCR, PaddleOCR |
| **Object tracking** | Object IDs across video frames | ByteTrack, DeepSORT |
| **Image–text models** | Zero-shot labels, search, captions | CLIP, BLIP |

### Key vision concepts

- **Data augmentation:** flips, crops, rotations and color jitter to make models robust.
- **Bounding boxes & IoU:** Intersection over Union measures how much a predicted box overlaps the true one.
- **Non-Maximum Suppression (NMS):** removes duplicate boxes around the same object.
- **Anchor-based vs. anchor-free detectors:** whether the model refines preset boxes or predicts boxes directly.
- **Metrics:** accuracy and top-5 for classification, mAP for detection, mIoU and Dice for segmentation.
- **Vision Transformers (ViT):** split the image into patches and treat them like tokens.

### Hands-On: Computer Vision

| # | Exercise | Tools |
|---|---|---|
| 6.1 | Image preprocessing & augmentation pipeline | OpenCV, Albumentations |
| 6.2 | Fine-tune a pretrained classifier on a custom dataset | torchvision, timm |
| 6.3 | Detect objects in images & webcam video | Ultralytics YOLO |
| 6.4 | Train a detector on your own labeled data | Roboflow / CVAT, YOLO |
| 6.5 | Segment medical or satellite images | U-Net, segmentation-models-pytorch |
| 6.6 | Zero-shot classification & image search | CLIP, Hugging Face |
| 6.7 | Extract text from documents / receipts | EasyOCR, PaddleOCR |

---

## 7. RNNs, LSTMs, GRUs

Networks for sequences such as text, speech, sensor readings and time series. They read one step at a time and carry a **hidden state** that works as memory of what came before.

**Prerequisites:** neural network basics (1), a framework (2).

**In this section:** [How an RNN works](#how-an-rnn-works) · [The variants](#the-variants) · [Sequence task shapes](#sequence-task-shapes) · [Limitations](#limitations-why-transformers-took-over) · [Hands-On: RNNs](#hands-on-rnns)

### How an RNN works

```
x₁ → [RNN] → h₁ → [RNN] → h₂ → [RNN] → h₃ → output
                 ↑ same weights reused at every step
```

At each step: `hₜ = tanh(W·xₜ + U·hₜ₋₁ + b)`

### The variants

| Model | Idea | Why it matters |
|---|---|---|
| **Vanilla RNN** | One hidden state passed forward | Simple, but forgets long-range context (vanishing gradients) |
| **LSTM** | Cell state plus input, forget and output gates | Remembers dependencies across long sequences |
| **GRU** | Update and reset gates only | Lighter than LSTM, often just as accurate |
| **Bidirectional RNN** | Reads the sequence forwards and backwards | Better context for tagging and classification |
| **Seq2Seq (encoder–decoder)** | One RNN encodes, another decodes | Translation, summarization; led to attention |

### Sequence task shapes

| Shape | Example |
|---|---|
| **Many-to-one** | Sentiment classification, time-series forecasting |
| **One-to-many** | Image captioning, music generation |
| **Many-to-many (aligned)** | Named-entity tagging, frame labeling |
| **Many-to-many (seq2seq)** | Machine translation |

### Limitations (why Transformers took over)

- They process steps one by one, so they can't run in parallel and train slowly.
- They still struggle with very long contexts, even with gates.
- Attention (topic 8) fixes both. RNNs remain useful for small, streaming and on-device time-series work.

### Hands-On: RNNs

| # | Exercise | Tools |
|---|---|---|
| 7.1 | Implement a vanilla RNN cell from scratch | NumPy |
| 7.2 | Character-level text generator | PyTorch |
| 7.3 | Sentiment analysis on IMDB reviews with an LSTM | PyTorch, Keras |
| 7.4 | Stock / weather time-series forecasting with GRU | PyTorch, Keras |
| 7.5 | Seq2seq with attention for a tiny translation task | PyTorch |

---

## 8. Attention & Transformers

The architecture behind every modern LLM (GPT, Claude, Llama), and also behind vision (ViT) and speech (Whisper) models. A Transformer reads **all tokens at once**, and **attention** lets each token look at every other token to decide what matters.

**Prerequisites:** neural network basics (1), a framework (2), RNNs (7), which show the problem Transformers solve.

**In this section:** [Why attention?](#why-attention) · [Self-attention: Q, K, V](#self-attention-q-k-v) · [Multi-head attention](#multi-head-attention) · [Positional encoding](#positional-encoding) · [The Transformer block](#the-transformer-block) · [Three Transformer families](#three-transformer-families) · [Hands-On: Transformers](#hands-on-transformers)

### Why attention?

| Problem with RNNs | How Transformers fix it |
|---|---|
| Read one token at a time, so training is slow | Process all tokens **in parallel** on a GPU |
| Forget words from far back | Any token can attend **directly** to any other, however far away |
| One hidden state has to hold everything | Each token builds its **own** context-aware representation |

Example: in *"The animal didn't cross the street because **it** was too tired"*, attention learns that **it** refers to *animal*.

### Self-attention: Q, K, V

Each token produces three vectors through learned weight matrices:

| Vector | Role | Analogy (library search) |
|---|---|---|
| **Query (Q)** | What this token is looking for | Your search question |
| **Key (K)** | What each token offers | Book titles on the shelf |
| **Value (V)** | The content each token passes on | The books' contents |

```
Attention(Q, K, V) = softmax( Q·Kᵀ / √dₖ ) · V
```

1. **Q·Kᵀ:** score how well each token's query matches every other token's key.
2. **÷ √dₖ:** scale the scores down so softmax doesn't saturate.
3. **softmax:** turn the scores into weights that add up to 1.
4. **· V:** take a weighted mix of the values. That is the token's new representation.

**Causal mask** (used in GPT-style models): each token may only attend to earlier tokens, so the model can't peek at the word it is supposed to predict.

### Multi-head attention

Run several attention "heads" in parallel, each with its own Q, K, V weights, then concatenate the results. Different heads learn different relationships: one tracks grammar, another tracks what a pronoun refers to, another tracks nearby words.

### Positional encoding

Attention by itself ignores word order ("dog bites man" = "man bites dog"). Position information is added to each token embedding:

| Method | Used in |
|---|---|
| **Sinusoidal** (fixed sin/cos waves) | Original Transformer (2017) |
| **Learned position embeddings** | BERT, GPT-2 |
| **RoPE** (rotary position embeddings) | Llama, Mistral, most modern LLMs |

### The Transformer block

```
tokens → embedding + position
   ↓
┌──────────────────────────────┐
│  Multi-head self-attention   │
│  + residual, LayerNorm       │
│  Feed-forward network (MLP)  │  × N blocks (e.g. 12 in GPT-2 small)
│  + residual, LayerNorm       │
└──────────────────────────────┘
   ↓
linear → softmax → next-token probabilities
```

- **Residual connections** (from ResNet) keep gradients flowing through deep stacks.
- **LayerNorm** keeps activations stable.
- **Feed-forward network** processes each token on its own, after attention has mixed in context.

### Three Transformer families

| Family | Attention | Trained to | Examples | Good for |
|---|---|---|---|---|
| **Encoder-only** | Sees the whole sentence (both directions) | Fill in masked words | BERT, RoBERTa | Classification, embeddings, search |
| **Decoder-only** | Causal: sees only the past | Predict the next token | GPT, Claude, Llama | Text generation, chat (LLMs) |
| **Encoder–decoder** | Encoder reads, decoder writes | Map input to output | T5, BART, Whisper | Translation, summarization, speech-to-text |

### Hands-On: Transformers

| # | Exercise | Tools |
|---|---|---|
| 8.1 | Implement scaled dot-product attention for a 4-token example by hand | NumPy |
| 8.2 | Add a causal mask and check that future tokens get zero weight | NumPy |
| 8.3 | Build multi-head attention as an `nn.Module` | PyTorch |
| 8.4 | Build one Transformer block (attention + MLP + residual + LayerNorm) | PyTorch |
| 8.5 | Visualize attention heads of a pretrained model | Hugging Face, BertViz |
| 8.6 | Use a pretrained BERT for classification, then GPT-2 for generation | Hugging Face Transformers |

**Next:** stack these blocks into a tiny GPT in [`3_gen_ai/` topic 3: LLMs](../3_gen_ai/README.md#3-large-language-models-llms).
