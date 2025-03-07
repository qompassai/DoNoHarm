# The Responsible Open Science Engines: Powering Minimally Invasive AI for Mentorship

## Authors
Matthew A. Porter, BSc<sup>1</sup>, Ariana Rowshan, BA<sup>2</sup>, Marcheta J. Hill, DO<sup>3<sup>, Dawn L. Laporte, MD<sup>2</sup>, Amiethab A. Aiyer, MD<sup>2</sup>

<sup>1</sup>Qompass AI, Spokane, WA  
<sup>2</sup>The Johns Hopkins University School of Medicine, Department of Orthopaedic Surgery, Baltimore, MD
<sup>3</sup>Arnot Ogden Medical Center Emergency Medicine Residency Program, Elmira, NY  
# 2025 RJOS Poster

[View Presentation](https://view.officeapps.live.com/op/embed.aspx?src=https://raw.githubusercontent.com/qompassai/r4r/main/r4r.pptx)


## Abstract
### Background
The rapid integration of generative artificial intelligence (genAI) into medical education has ushered in transformative changes, offering innovative tools and methodologies that enhance learning and practice. AI applications, such as adaptive learning platforms and virtual patient simulations, have become increasingly prevalent, providing personalized and immersive educational experiences. These advancements not only improve educational outcomes but also address critical needs across diverse learner populations. 

However, the swift adoption of AI technologies has highlighted significant ethical considerations, particularly concerning bias, transparency, and equitable access. In this context, our pilot study focused on harnessing genAI to enhance mentorship for aspiring orthopedic surgeons, especially those from marginalized backgrounds or institutions lacking dedicated orthopedic residencies. By developing a prototype model that delivers high-quality, personalized mentorship content, we strive to democratize access to essential resources, ensuring that all candidates have the opportunity to succeed, regardless of their circumstances.


### Methods
In response to noticeably increasing cost of AI medical education, our study focuses on the deployment of quantized, small-scale AI models on-device. This approach aims to ensure accessibility and equity, particularly for underfunded institutions and learners from non-traditional, disabled, and underrepresented minority populations. We began by selecting open-source AI models renowned for their efficacy in educational contexts. To optimize these models for deployment on resource-constrained hardware, we employed quantization techniques, which reduce the precision of the model's parameters, thereby decreasing memory usage and computational demands without significantly compromising performance. Our deployment environment comprised consumer-grade Linux computers, reflecting hardware commonly available in industry and increasingly academia. We utilized standard Linux distributions, ensuring all software dependencies were met. To enhance computational efficiency, we leveraged NVIDIA's Compute Unified Device Architecture (CUDA 12.8) for on-device acceleration, enabling the models to utilize available GPU resources. The quantized models were integrated into the system in transient sandboxed environments as well as via hard-coded web-based application program interfaces (APIs)  to streamline deployment and ensure consistency across various infrastructures.


### Results

* Education

[Equitable Open AI Curriculum](https://github.com/qompassai/Equator)

[R3 | Open-Weight Small MultiModal Finetune of LLaMA3](https://huggingface.co/qompass/r3)

* Safety

[Safety guardrails via NIST AI Risk Management Framework ](https://github.com/qompassai/Nautilus/blob/main/RedTeam/RedAI/NIST/AI_RMF_Playbook.pdf)

[Dioptra | One NIST-endorsed tool in our purple evaluation process](https://github.com/qompassai/Nautilus/tree/main/RedTeam/RedAI/NIST/Qompass_Dioptra)

[Kyber Odyssey- Post Quantum Cryptography to secure legacy software & AI deployment](https://github.com/qompassai/KO)

* Use-Cases

[AI Data Management Protocol Walkthrough](https://www.youtube.com/watch?v=T-XGHgaJIPU&t=234s)

[Ollie | Small Multimodal Model with Web Search Tool Calling](https://www.youtube.com/watch?v=OvxrfwC3CKY&t=9s)

[Vale | SMM for MultiLingual Patient Education](https://www.youtube.com/watch?v=q-2EL-ajNKc&t=8s)



* Increasing SMM Efficiency

TLDR: Using consumer-grade hardware to improve small Open Neural Network Exchange (ONNX) video inference models:

**BiRefNet-general-bb_swin_v1_tiny-epoch_232**

```bash
# BiRefNet is capable of handling background removal tasks for images and videos via efficient inference on-devices. It uses advanced neural network architectures like Swin Transformer.

trtexec --onnx=BiRefNet-general-bb_swin_v1_tiny-epoch_232.onnx --saveEngine=BiRefNet-general.trt --fp16 --memPoolSize=workspace:4096 --verbose --useCudaGraph --useSpinWait --noDataTransfers --builderOptimizationLevel=5 --tilingOptimizationLevel=3 --profilingVerbosity=detailed --exportTimes=timing.json --exportProfile=profile.json --exportLayerInfo=layers.json --separateProfileRun --avgRuns=100 --persistentCacheRatio=1.0 --maxAuxStreams=4 --warmUp=500 --duration=60 --iterations=100 --device=0}
```

**Isnet-anime**

```bash
# Isnet-anime is optimized specifically to detect and remove backgrounds in scenarios involving anime or secondary characters. This makes it ideal for artistic or creative projects where the input data involves stylized or animated visuals.

trtexec --onnx=isnet-anime.onnx --saveEngine=BiRefNet-general.trt --fp16 --memPoolSize=workspace:4096 --verbose --useCudaGraph --useSpinWait --builderOptimizationLevel=5 --tilingOptimizationLevel=3 --profilingVerbosity=detailed --exportTimes=timing.json --exportProfile=profile.json --exportLayerInfo=layers.json --separateProfileRun --avgRuns=100 --persistentCacheRatio=1.0 --maxAuxStreams=4 --warmUp=500 --duration=60 --iterations=100 --device=0 --exposeDMA  --timeDeserialize --timeRefit}
```

```
Where:
- --onnx} represents the input ONNX model path
- --saveEngine} specifies the output TensorRT engine path
- --fp16} enables half-precision floating point optimization
- --memPoolSize} allocates workspace memory in MiB
- --builderOptimizationLevel} sets optimization level (1-5)
- --tilingOptimizationLevel} configures tiling optimization (0-4)
- --avgRuns} defines the number of inference runs for averaging
- --warmUp} specifies warm-up iterations before timing
- --duration} sets profiling duration in seconds
- --iterations} defines the number of inference iterations
- --maxAuxStreams} configures concurrent CUDA streams
- --persistentCacheRatio} sets cache persistence (0-1)
- --exposeDMA enables the exposure of Direct Memory Access (DMA) for performance.
- --timeDeserialize enables timing measurement for engine deserialization.
- --timeRefit enables timing for the engine refitting process.
```
**Run with TensorRT 10.8, CUDA 12.8, nvidia-open-dkms on Arch Linux-Zen 6.13-4-1 x86_64**


# FAQ

### Q: How would you describe AI to someone who's "not technical"?
### A: We dislike identifying people as technical or not technical. This sort of language is othering and unkind. AI is like cake, not all cakes are created equal, but they can all be great in their own ways. Yann LeCun, Turing Award winner, Meta's Chief AI Scientist and a professor at NYU simplified the complex world of AI by comparing it to a layered cake. We endeavor to do the same :)

## **AI As Cake From Top to Bottom**

**Referencing the left most image in the poster**

[View Presentation](https://view.officeapps.live.com/op/embed.aspx?src=https://raw.githubusercontent.com/qompassai/r4r/main/r4r.pptx)

### Governance & Auditability (The Decorative Frosting)
- **Transparent Decision Logs**: Like a recipe book recording each step of the baking process
- **Regulatory Compliance**: Following food safety standards and baking regulations
- **Explainability**: Like listing ingredients and nutritional information on the box

### Operational Independence (The Master Baker's Expertise)
- **Self-Learning**: Like perfecting recipes through practice and feedback
- **Autonomous Decisions**: Knowing when the cake is done without using a timer
- **Scalability**: Adjusting recipe portions for different serving sizes

### External Interactions (The Kitchen Equipment)
- **API Integrations**: Like connecting different appliances in a professional kitchen
- **Automated Workflows**: Similar to using a stand mixer for consistent results
- **Real-Time Decision Making**: Like adjusting oven temperature while baking

### Interaction Interface (The Cake Filling)
- **Multi-Modal Support**: Like different layers of filling - cream, fruit, and chocolate
- **User Input Processing**: Like following customer specifications for custom cakes
- **Personalization**: Adjusting flavors and decorations to individual taste

### Ethics & Safety (The Quality Control)
- **Privacy Protection**: Like keeping secret recipes safe
- **Bias Detection**: Testing for balanced flavors and proper texture
- **Harm Prevention**: Ensuring ingredients are fresh and allergen-free

### Knowledge Base (The Recipe Collection)
- **Contextualization & Retrieval**: Like knowing which recipes work for different occasions
- **Structured & Unstructured Data**: Organized recipes and cooking intuition
- **Domain-Specific Enrichment**: Specializing in specific types of baking

### Retrieval Augmented Generation (RAG) (The Essential Ingredients)
- **Fact-Checking**: Like measuring ingredients precisely for consistent results

### The Model (LLM/SMM/SLM/LMM) (The Basic Cake Batter)
- **Reasoning & Adaptability**: Like how basic batter can become different cakes
- **Generative Capabilities**: Transforming raw ingredients into finished cakes
- **Real-Time Data Retrieval**: Gathering fresh ingredients as needed
- **Contextual Augmentation**: Adding flavors and textures to enhance the base
- **Training & Fine-Tuning**: Perfecting the recipe through multiple iterations

### Q: How do you mitigate against bias?

**TLDR - we do math to make AI ethically useful**

### A: We delineate between mathematical bias (MB) - a fundamental parameter in neural network equations - and algorithmic/social bias (ASB). While MB is optimized during model training through backpropagation, ASB requires careful consideration of data sources, model architecture, and deployment strategies. We implement attention mechanisms for improved input processing and use legal open-source data and secure web-search APIs to help mitigate ASB. 

 [AAMC AI Guidelines | One way to align AI against ASB](https://www.aamc.org/about-us/mission-areas/medical-education/principles-ai-use)

 ### AI Math at a glance

## Forward Propagation Algorithm

$$
y = w_1x_1 + w_2x_2 + ... + w_nx_n + b
$$

Where:

- $y$ represents the model output
- $(x_1, x_2, ..., x_n)$ are input features
- $(w_1, w_2, ..., w_n)$ are feature weights
- $b$ is the bias term
### Neural Network Activation

For neural networks, the bias term is incorporated before activation:

$$
z = \sum_{i=1}^{n} w_ix_i + b
$$
$$
a = \sigma(z)
$$

Where:
- $z$ is the weighted sum plus bias
- $a$ is the activation output
- $\sigma$ is the activation function

### Attention Mechanism- aka what makes the Transformer (The "T" in ChatGPT) powerful

* [Attention High level overview video](https://www.youtube.com/watch?v=fjJOgb-E41w)

* [Attention Is All You Need Arxiv Paper](https://arxiv.org/abs/1706.03762)

The Attention mechanism equation is:

$$
\text{Attention}(Q, K, V) = \text{softmax}\left( \frac{QK^T}{\sqrt{d_k}} \right) V
$$

Where:
- $Q$ represents the Query matrix
- $K$ represents the Key matrix
- $V$ represents the Value matrix
- $d_k$ is the dimension of the key vectors
- $\text{softmax}(\cdot)$ normalizes scores to sum to 1

### How is it $0 cost?

* We self-host models and we thoughtfully implement open source software and write our own code. All hardware was already purchased prior to the grant being awarded.
* We public-source the code-bases under dual-license at no cost to learners or educators not intending on enterprise-grade commercial use. We make $0 in public-sourcing our code.
* We make efficient use of our free memberships to the NVIDIA, Meta, Groq, and Github developer programs

### Q: Do I have to buy a Linux computer to use this? I don't have time for that!
### A: No. You can run Linux and/or the tools we share alongside your existing operating system:
    
* Windows users can use Windows Subsystem for Linux [WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
* Mac users can use [Homebrew](https://brew.sh/)
* The code-base instructions were developed with both beginners and advanced users in mind.

### Q: Do you have to get a masters in AI?
### A: Not if you don't want to. To get competent enough to get past ChatGPT dependence at least, you just need a computer and a beginning's mindset. Huggingface is a good place to start. 
* [Huggingface](https://docs.google.com/presentation/d/1IkzESdOwdmwvPxIELYJi8--K3EZ98_cL6c5ZcLKSyVg/edit#slide=id.p)

### Q: What makes a "small" AI model?
### A: AI models ~=10 billion(10B) parameters and below. For comparison, OpenAI's GPT4o contains approximately 200B parameters.

## What a Dual-License means

### Protection for Vulnerable Populations

The dual licensing aims to address the cybersecurity gap that disproportionately affects underserved populations. As highlighted by recent attacks[^1], low-income residents, seniors, and foreign language speakers face higher-than-average risks of being victims of cyber attacks. By offering both open-source and commercial licensing options, we encourage the development of cybersecurity solutions that can reach these vulnerable groups while also enabling sustainable development and support.

### Preventing Malicious Use

The AGPL-3.0 license ensures that any modifications to the software remain open source, preventing bad actors from creating closed-source variants that could be used for exploitation. This is especially crucial given the rising threats to vulnerable communities, including children in educational settings. The attack on Minneapolis Public Schools, which resulted in the leak of 300,000 files and a $1 million ransom demand, highlights the importance of transparency and security[^8].

### Addressing Cybersecurity in Critical Sectors

The commercial license option allows for tailored solutions in critical sectors such as healthcare, which has seen significant impacts from cyberattacks. For example, the recent Change Healthcare attack[^4] affected millions of Americans and caused widespread disruption for hospitals and other providers. In January 2025, CISA[^2] and FDA[^3] jointly warned of critical backdoor vulnerabilities in Contec CMS8000 patient monitors, revealing how medical devices could be compromised for unauthorized remote access and patient data manipulation.
### Supporting Cybersecurity Awareness

The dual licensing model supports initiatives like the Cybersecurity and Infrastructure Security Agency (CISA) efforts to improve cybersecurity awareness[^7] in "target rich" sectors, including K-12 education[^5]. By allowing both open-source and commercial use, we aim to facilitate the development of tools that support these critical awareness and protection efforts.

### Bridging the Digital Divide

The unfortunate reality is that a number of individuals and organizations have gone into a frenzy in every facet of our daily lives[^6]. These unfortunate folks identify themselves with their talk of "10X" returns and building towards Artificial General Intelligence aka "AGI" while offering GPT wrappers. Our dual licensing approach aims to acknowledge this deeply concerning predatory paradigm with clear eyes while still operating to bring the best parts of the open-source community with our services and solutions.

### Recent Cybersecurity Attacks

Recent attacks underscore the importance of robust cybersecurity measures:

- The Change Healthcare cyberattack in February 2024 affected millions of Americans and caused significant disruption to healthcare providers.
- The White House and Congress jointly designated October 2024 as Cybersecurity Awareness Month. This designation comes with over 100 actions that align the Federal government and public/private sector partners are taking to help every man, woman, and child to safely navigate the age of AI. 

By offering both open-source and commercial licensing options, we strive to create a balance that promotes innovation and accessibility while also providing the necessary resources and flexibility to address the complex cybersecurity challenges faced by vulnerable populations and critical infrastructure sectors.

[^1]: [International Counter Ransomware Initiative 2024 Joint Statement](https://www.whitehouse.gov/briefing-room/statements-releases/2024/10/02/international-counter-ransomware-initiative-2024-joint-statement/)
[^2]: [Contec CMS8000 Contains a Backdoor](https://www.cisa.gov/sites/default/files/2025-01/fact-sheet-contec-cms8000-contains-a-backdoor-508c.pdf)
[^3]: [CISA, FDA warn of vulnerabilities in Contec patient monitors](https://www.aha.org/news/headline/2025-01-31-cisa-fda-warn-vulnerabilities-contec-patient-monitors)
[^4]: [The Top 10 Health Data Breaches of the First Half of 2024](https://www.chiefhealthcareexecutive.com/view/the-top-10-health-data-breaches-of-the-first-half-of-2024)
[^5]: [CISA's K-12 Cybersecurity Initiatives](https://www.cisa.gov/K12Cybersecurity)
[^6]: [Federal Trade Commission Operation AI Comply: continuing the crackdown on overpromises and AI-related lies](https://www.ftc.gov/business-guidance/blog/2024/09/operation-ai-comply-continuing-crackdown-overpromises-ai-related-lies)
[^7]: [A Proclamation on Cybersecurity Awareness Month, 2024 ](https://www.whitehouse.gov/briefing-room/presidential-actions/2024/09/30/a-proclamation-on-cybersecurity-awareness-month-2024/)
[^8]: [Minneapolis school district says data breach affected more than 100,000 people](https://therecord.media/minneapolis-schools-say-data-breach-affected-100000/)

