# ⚡ ZatcaOracle v2.0 
**The Ultra-Fast ZATCA Phase 2 E-Invoicing Engine**

ZatcaOracle is a premium, high-performance TLV encoding and cryptographic validation engine engineered for Saudi Arabia's **ZATCA Phase 2 (Integration Phase)**. Built on a **.NET 10 Native AOT** architecture and deployed via **Zero-Shell Distroless** containers, it delivers unparalleled speed, security, and absolute data residency compliance.

---

## 📊 Enterprise Performance Metrics

*   **Logic Latency:** P99 internal execution is verified at **0.76ms** via Native AOT.
*   **Data Residency:** 100% hosted in **Google Cloud (me-central2, Dammam, KSA)** to strictly meet Saudi cybersecurity regulations.
*   **Throughput Capacity:** Stress-tested for **3,300+ TPS** per instance to handle high-traffic billing cycles.
*   **Resource Density:** Operates on a minimal **11MB footprint**—20x more efficient than the industry average.
*   **Security Hardening:** **Zero-Shell Distroless (Chiseled)** environment eliminates 95% of common attack surfaces.

---

## 📶 Performance & Network Architecture

While our internal engine executes in **<1ms**, users testing via the RapidAPI Hub may see an average Round Trip Time (RTT) of ~400ms. This is due to the RapidAPI proxy originating from eu-west-1.

*   **For Production:** Enterprise clients requiring true **<10ms end-to-end latency** can request **Direct Access**. This bypasses the proxy and hits our **Dammam-based cluster** directly, ensuring maximum performance and legal adherence to Saudi Data Residency laws.

---

## 🚀 Integration Paths

We offer two distinct paths to ensure seamless onboarding and high-frequency production scaling:

### 1. The Magic Path (Zero-Friction Onboarding)
Ideal for initial testing and SME implementation. Pass your raw certificate, and the Oracle automatically extracts **Tag 8 (Public Key)** and **Tag 9 (Signature)**.
*   **Execution Time:** ~1.2ms.
*   **Input Requirement:** `certificate` string.

### 2. The Pro Path (High-Frequency Production)
Designed for enterprise scale. Bypass extraction logic by passing your cached tags directly to the engine.
*   **Execution Time:** **0.76ms**.
*   **Input Requirement:** `publicKey` and `certificateStamp` strings.

---

## 🤖 AI Agent Integration (MCP)

ZatcaOracle is **MCP-native**. If you are building with **Cursor**, **Claude**, or **GitHub Copilot**, use this prompt to automate your integration:

> *"Read the API specification at `https://abdelghani-moussaid.github.io/zatca-phase-2-agent-integration/llms.txt`. Implement a service that uses the 'Magic Path' to extract the public key and certificate stamp, then caches those values to use the 'Pro Path' for all subsequent requests to `/api/v1/generate`. Ensure the timestamp follows the No-Z rule."*

---

## 🛡️ Strict Validation & Compliance Rules

To avoid **400 Bad Request** errors and ensure your QR codes are legally valid per official ZATCA documentation:

1.  **15-Digit VAT Rule:** The seller's VAT number must be exactly 15 numeric characters.
2.  **No-Z Rule (Timestamp):** Timestamps must strictly match `YYYY-MM-DDTHH:mm:ss`. Do **not** include the 'Z' (Zulu) suffix or timezone offsets.
3.  **Signature Validation:** A `SIGNATURE_INVALID` error indicates a cryptographic mismatch between the Hash and Public Key. Cross-reference Tags 6, 7, and 8.

---

## 🔗 Quick Links
*   **[Enterprise Technical Brief (PDF)](https://abdelghani-moussaid.github.io/zatca-phase-2-agent-integration/ZatcaOracle_v2.0_Enterprise_Technical_Brief.pdf)**
*   **[AI-Readable Specification (llms.txt)](https://abdelghani-moussaid.github.io/zatca-phase-2-agent-integration/llms.txt)**
