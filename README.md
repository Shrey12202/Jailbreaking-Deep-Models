# Jailbreaking Deep Models

### Deep Learning Project 3  
Shrey Vyas, Shabad Vaswani, Vidhi Ajbani  
New York University  
Contact: sbv2019@nyu.edu, sdv2034@nyu.edu, vba2015@nyu.edu

GitHub Repository: [https://github.com/Shrey12202/Jailbreaking-Deep-Models](https://github.com/Shrey12202/Jailbreaking-Deep-Models)

---

## 📄 Abstract

This project investigates the vulnerability of deep neural networks to adversarial attacks—small, carefully engineered perturbations that cause models to make incorrect predictions while appearing unchanged to the human eye. We focus on attacking a pre-trained ResNet-34 model on ImageNet-1K using:

- Fast Gradient Sign Method (FGSM)
- Projected Gradient Descent (PGD)
- Patch-based Localized Attacks (Standard and PGD-based)

All attacks respect **L∞ norm constraints** to ensure imperceptibility. We also test attack transferability on DenseNet-121. Our findings expose systemic fragility in modern image classifiers and emphasize the importance of robust evaluation.

---

## 📝 Overview

CNNs like ResNet-34 perform well on benchmarks such as ImageNet-1K but are vulnerable to small, calculated input perturbations. These vulnerabilities threaten real-world applications such as medical imaging, autonomous driving, and security systems.

Our study systematically explores:
- Pixel-wise attacks (FGSM, PGD)
- Localized patch attacks (Patch, Patch-PGD)
- Transferability to DenseNet-121

We evaluate effectiveness using **top-1** and **top-5 accuracy** metrics and visualize adversarial samples with a custom **denormalization utility**.

---

## 🛠️ Methodology

### ✅ Model and Dataset
- **Model**: Pretrained ResNet-34 and DenseNet-121 from TorchVision.
- **Dataset**: Subset of 500 images from 100 ImageNet-1K classes.

### ✅ Attack Methods
1. **FGSM**: Single-step gradient attack.
2. **BIM/IFGSM**: Iterative FGSM.
3. **Targeted FGSM**: Directs predictions to a target class.
4. **PGD**: Strongest iterative attack with random start.
5. **Patch Attack**: Localized 32×32 pixel attack.
6. **Patch-PGD**: Iterative patch attack using PGD.

---

## 📊 Results

| Dataset                        | Model        | Top-1 Acc | Top-5 Acc |
|---------------------------------|-------------|----------|----------|
| Original Test Set               | ResNet-34   | 76.0%    | 94.2%    |
| Adversarial Test Set (FGSM)     | ResNet-34   | 43.2%    | 63.2%    |
| Adversarial Test Set (IFGSM)    | ResNet-34   | 42.6%    | 56.2%    |
| Adversarial Test Set (TFGSM)    | ResNet-34   | 25.4%    | 48.0%    |
| Adversarial Test Set (PGD)      | ResNet-34   | 0.4%     | 6.0%     |
| Adversarial Test Set (Patch)    | ResNet-34   | 10.4%    | 55.0%    |
| Adversarial Test Set (Patch-PGD)| ResNet-34   | 11.0%    | 30.6%    |
| Original Test Set               | DenseNet-121| 74.8%    | 93.6%    |
| FGSM Transferred                | DenseNet-121| 0%       | 0%       |
| PGD Transferred                 | DenseNet-121| 39.4%    | 63.8%    |
| Patch Attack Transferred        | DenseNet-121| 71.2%    | 90.4%    |

**Key Takeaways**:
- PGD is the most effective attack, nearly collapsing ResNet-34’s performance.
- Patch-based attacks are surprisingly effective despite modifying only small regions.
- FGSM does not transfer well to DenseNet-121, while PGD shows moderate transferability.

---

## 🧠 Lessons Learned
- Simple gradient manipulation (FGSM) can destabilize robust models.
- Iterative refinement (BIM, PGD) significantly increases attack success.
- Localized attacks (Patch, Patch-PGD) can be highly disruptive while remaining stealthy.
- Transferability depends on attack type; PGD is the most transferable.

---

## 📚 References

1. Goodfellow, I. J., Shlens, J., & Szegedy, C. (2015). Explaining and harnessing adversarial examples. ICLR.
2. Kurakin, A., Goodfellow, I., & Bengio, S. (2016). Adversarial examples in the physical world. arXiv:1607.02533.
3. Madry, A., et al. (2018). Towards deep learning models resistant to adversarial attacks. ICLR.
4. Brown, T., et al. (2017). Adversarial patch. arXiv:1712.09665.
5. PyTorch Vision Docs: https://pytorch.org/vision/stable/models.html
6. Deng, J., et al. (2009). ImageNet: A large-scale hierarchical image database. CVPR.

---

## ✅ How to Run
1. Clone this repository.
2. Install dependencies from `requirements.txt`.
3. Run the provided Jupyter Notebooks or Python scripts to reproduce results.

---

## ✅ License
This repository is for academic purposes only.

---

