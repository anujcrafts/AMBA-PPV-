# AMBA-PPV: Adaptive Multimodal Biometric Authentication — Privacy Preserving Voting

A research prototype implementing a confidence-aware Cross-Modal Transformer that dynamically fuses face and fingerprint representations, incorporates multimodal presentation-attack detection, and separates biometric authentication from anonymous vote casting through privacy-preserving tokenization.

## Architecture

**Two-Portal System:**
- **Admin Portal** — Full system access (election management, voter enrollment, audit, analytics)
- **User Portal** — Limited access (biometric verification, vote casting, receipt viewing)

**Five Core Modules:**
1. **Intelligent Face Recognition** — SCRFD/RetinaFace → ViT + ArcFace
2. **Deep Fingerprint Recognition** — Gabor Enhancement → Deep CNN Encoder
3. **Cross-Modal Fusion (ACM-BF)** — Adaptive Cross-Modal Biometric Fusion
4. **Anti-Spoofing (M-PAD)** — Multimodal Presentation Attack Detection
5. **Privacy-Preserving Voting** — Cancelable templates + anonymous tokens + tamper-evident ledger

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + TypeScript + Tailwind CSS |
| Backend | FastAPI (Python 3.11+) |
| Database | PostgreSQL 15+ |
| ML Framework | PyTorch |
| Face Recognition | InsightFace (SCRFD + ArcFace) |
| Blockchain | Custom Python hash-chain ledger |

## Quick Start

### 1. One-Click Launch (Windows)
Double-click `start.bat` or run:
```cmd
start.bat
```
Or in PowerShell:
```powershell
.\run.ps1
```

### 2. Manual Launch
**Backend (Terminal 1):**
```bash
cd backend
py -3.13 seed.py
py -3.13 -m uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```

**Frontend (Terminal 2):**
```bash
cd frontend
npm.cmd run dev
```

### 3. Docker Compose
```bash
docker compose up --build
```

## System URLs & Default Credentials

- **Web Portal:** [http://localhost:3000](http://localhost:3000)
- **API Swagger Docs:** [http://localhost:8000/docs](http://localhost:8000/docs)

| Role | Unique Number (Username) | Password | Description |
|------|--------------------------|----------|-------------|
| **Admin** | `AMBA-ADMIN-01` (or `admin`) | `AdminPassword@123` (or `admin`) | Full administrative, election management, analytics, and settings access |
| **Enrolled Voter** | `AMBA-VOTER-01` (or `voter`) | `VoterPassword@123` (or `voter`) | Pre-enrolled with biometric face and fingerprint templates |
| **New Voter** | `AMBA-VOTER-02` | `VoterPassword@123` | Registered voter awaiting biometric enrollment |

## Running Tests
Run the automated test suite covering Paillier homomorphic encryption, BioHashing cancelable templates, biometric token vault, blockchain Merkle tree, and cryptographically certified PDF export:
```bash
cd backend
py -3.13 -m pytest tests/test_all_innovations.py -v
```

## Research Experiments
See `backend/ml/evaluation/` for experiment scripts including:
- Model comparison (Face-only, Fingerprint-only, CNN fusion, Transformer fusion, ACM-BF)
- Ablation study
- Metrics: Accuracy, Precision, Recall, F1, FAR, FRR, EER, TAR@FAR, latency, FPS

## License
Research prototype — for academic use only.
