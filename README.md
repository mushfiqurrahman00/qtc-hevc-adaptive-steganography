# QTC-Domain Adaptive Secure Video Steganography for HEVC (H.265)

An adaptive QTC-domain video steganography framework for HEVC (H.265) that investigates CNN-guided detection risk, rate-distortion cost, texture information, and STC-based embedding.

> **Status:** Undergraduate Thesis — In Progress

---

## Overview

This project investigates secure data hiding in compressed HEVC/H.265 video by using the **Quantized Transform Coefficient (QTC)** domain as the embedding domain.

The proposed framework aims to construct an adaptive embedding cost by combining:

1. CNN-based detection risk
2. Rate-distortion (RD) information
3. Texture information

The resulting adaptive cost is provided to a **Syndrome-Trellis Code (STC)** based embedding process to select a cost-efficient modification pattern for the secret payload.

The modified QTC coefficients are then used to reconstruct the stego video through HEVC encoding.

The primary research objective is to investigate whether a content-adaptive, security-aware QTC embedding strategy can improve the security-capacity-quality trade-off of HEVC video steganography.

---

## Research Problem

Video steganography in compressed video codecs must balance several competing requirements:

- Security against steganalysis
- Visual and perceptual quality
- Embedding capacity
- Rate/bitrate overhead
- Computational feasibility

Modifying transform coefficients can introduce statistical and structural artifacts that may make a stego video detectable.

Traditional embedding-cost methods generally model distortion, texture, coding effects, or related properties. However, there is limited evidence of a security-aware adaptive embedding strategy in the HEVC QTC domain that explicitly incorporates information derived from a deep-learning steganalyzer into the embedding cost.

This project investigates such a framework.

---

## Proposed Approach

The proposed framework follows the general pipeline:

```text
                 Cover Video
                      |
                      v
                HEVC Encoder
                      |
                      v
        Quantized Transform Coefficients
                     (QTC)
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
       CNN Risk    RD Cost     Texture
          |           |           |
          +-----------+-----------+
                      |
                      v
              Adaptive Cost
                 Function
                      |
                      v
                     STC
                      |
                      v
              Modified QTC
                      |
                      v
              HEVC Re-encoding
                      |
                      v
                 Stego Video
