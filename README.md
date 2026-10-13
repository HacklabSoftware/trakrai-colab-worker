# TrakrAI GPU worker for Google Colab

Lend a Google Colab GPU to your factory's model training in [TrakrAI](https://ai.trakr.live).

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HacklabSoftware/trakrai-colab-worker/blob/main/trakrai-colab-worker.ipynb)

## How it works

1. Click the badge above. Colab opens the notebook and asks for a T4 GPU.
2. Choose **Runtime → Run all**. The cell prints an approval link and a short code.
3. Open the link, sign in to TrakrAI and click **Approve**. The cell connects by itself.

The request can also be approved from **Model training → Colab GPU** in TrakrAI, where the code can be typed by hand. It expires after 15 minutes. If you already created a pairing code in TrakrAI, paste it into the notebook's `PAIRING_CODE` field instead and no approval is needed.

The worker connects to your TrakrAI site, runs only jobs for the factory that approved it, and stops when you stop the notebook. It uses your own Colab compute units; TrakrAI never sees your Google account.

## Requirements

- A Colab account with a paid plan or a positive compute-unit balance. Colab's terms do not allow background workers on the free tier.
- A TrakrAI login with model-admin access to a factory, or a colleague who has it and can approve the request.

## What the notebook does

The single code cell asks TrakrAI for approval (or exchanges a pairing code), receives a worker token, downloads the worker code from your TrakrAI site, and runs it on the Colab GPU until you stop the cell. Nothing is installed outside the Colab runtime, and the token is stored only in the runtime's temporary disk.
