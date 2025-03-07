# First, Do No Harm: On Making AI Safe, Secure, and Trustworthy
## Authors
Matthew A. Porter, BSc<sup>1</sup>, Henry Mroch, MD<sup>2</sup>

<sup>1</sup>Qompass AI, Spokane, WA  
<sup>2</sup>Elson S. Floyd College of Medicine, Spokane, WA
# 2025 WSU Research Symposium

**See the results for yourself by clicking the image below!**
[![First, Do No Harm](dnhthumb.jpg)](https://www.youtube.com/watch?v=BywchwByGLA)



## Abstract
[View Presentation](https://view.officeapps.live.com/op/embed.aspx?src=https://raw.githubusercontent.com/qompassai/DoNoHarm/main/donoharm.pptx)
### Background
Abstract

The integration of generative artificial intelligence (genAI) into software ecosystems has led to rapid advancements in secure, efficient, and innovative applications. This transformative shift necessitates robust cryptographic safeguards to ensure trust, privacy, and reliability. In our project, "First, Do No Harm," we explore the intersection of post-quantum cryptography (PQC), Unreal Engine, and our custom Neovim implementation, "Diver," enhanced with rose.nvim—a plugin designed to facilitate AI model selection and secure interaction. By leveraging OpenSSL with post-quantum cryptographic algorithms, we ensure that AI communications remain resilient against future cryptographic threats. Our work emphasizes secure key exchange mechanisms and encryption methodologies that protect sensitive AI-driven interactions from adversarial compromise. To demonstrate the application of these technologies in immersive learning and development environments, we have integrated our secure AI framework into Unreal Engine, enabling the deployment of real-time, interactive AI-assisted simulations.
Furthermore, "Diver" extends Neovim with rose.nvim, providing a streamlined interface for locally hosted AI models and secure web-based APIs. This setup allows developers and researchers to interact with AI tools in a controlled, privacy-preserving manner, reinforcing best practices in security and ethical AI deployment. Our approach ensures accessibility while prioritizing safety, equity, and transparency in AI-driven development. Through this initiative, we aim to set new standards for AI safety, security, and trustworthiness, ensuring that generative AI can be harnessed responsibly across diverse domains. By integrating cryptographic resilience, high-performance computing, and developer-friendly tools, our project offers a blueprint for the future of secure AI implementation.




### Methods
To address the increasing security concerns in AI-driven applications, we implemented a robust methodology centered on cryptographic integrity, real-time interactivity, and developer accessibility. Our approach prioritizes efficiency without compromising security, ensuring that AI models are deployed safely and effective. For performance optimization, we serve AI models capable of operating on a single consumer grade GPU operating on Arch Linux with CUDA 12.8, TensorRT 10.8, and Pytorch 2.6-cu126. We began by integrating OpenSSL with post-quantum cryptographic (PQC) algorithms, selecting those with demonstrated resilience against both classical and quantum threats. Our cryptographic framework ensures that AI model interactions—whether hosted locally or via secure APIs—remain protected through advanced key exchange protocols and end-to-end encryption techniques. Our custom Neovim implementation, "Diver," incorporates rose.nvim as an AI model interface, providing a seamless experience for researchers and developers. The plugin enables users to select AI models locally or interact with them via secure web-based APIs. All web interactions are secured using PQC-backed TLS encryption to mitigate emerging cryptographic threats. The models operate within sandboxed environments, ensuring secure execution and isolation from the host system. By structuring AI deployment within controlled, cryptographically secure ecosystems, we aim to establish a foundation for AI trustworthiness. Our methodology underscores the importance of privacy, security, and accessibility in AI-driven software development, ensuring that innovations remain both powerful and responsible.


### Results

<details><summary>Education</summary>

[First, Do No Harm](https://www.youtube.com/watch?v=BywchwByGLA&feature=youtu.be)

[Equitable Open AI Curriculum](https://github.com/qompassai/Equator)

[R3 | Open-Weight Small MultiModal Finetune of LLaMA3](https://huggingface.co/qompass/r3)

[Qompass Diver](https://github.com/qompassai/Diver)
</details>
<details><summary>Safety</summary>

[Qompass Sojourn | Deploying models, unreal and otherwise](https://github.com/qompassai/sojourn)

[Safety guardrails via NIST AI Risk Management Framework ](https://github.com/qompassai/Nautilus/blob/main/RedTeam/RedAI/NIST/AI_RMF_Playbook.pdf)

[Dioptra | One NIST-endorsed tool in our purple evaluation process](https://github.com/qompassai/Nautilus/tree/main/RedTeam/RedAI/NIST/Qompass_Dioptra)

[Kyber Odyssey- Post Quantum Cryptography to secure legacy software & AI deployment](https://github.com/qompassai/KO)
</details>

<details>* <summary>Use-Cases</summary>

[AI Data Management Protocol Walkthrough](https://www.youtube.com/watch?v=T-XGHgaJIPU&t=234s)

[Ollie | Small Multimodal Model with Web Search Tool Calling](https://www.youtube.com/watch?v=OvxrfwC3CKY&t=9s)

[Vale | SMM for MultiLingual Patient Education](https://www.youtube.com/watch?v=q-2EL-ajNKc&t=8s)
</details>

<details>
<summary>On Increasing SMM Efficiency</summary>

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
</details>

# FAQ


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

