# TrakrAI GPU worker for Google Colab

Lend a Google Colab GPU to your factory's model training in [TrakrAI](https://ai.trakr.live).

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jainhardik120/trakrai-colab-worker/blob/main/trakrai-colab-worker.ipynb)

## How it works

1. Click the badge above. Colab opens the notebook and asks for a T4 GPU.
2. In TrakrAI, open **Model training → Colab GPU** and click **Create pairing code**.
3. Paste the code into the notebook and choose **Runtime → Run all**.

The worker connects to your TrakrAI site, runs only jobs for the factory that created the code, and stops when you stop the notebook. It uses your own Colab compute units; TrakrAI never sees your Google account.

## Requirements

- A Colab account with a paid plan or a positive compute-unit balance. Colab's terms do not allow background workers on the free tier.
- A TrakrAI account with model-admin access to a factory.

## What the notebook does

The single code cell exchanges the pairing code for a worker token, downloads the worker code from your TrakrAI site, and runs it on the Colab GPU until you stop the cell. Nothing is installed outside the Colab runtime, and the token is stored only in the runtime's temporary disk.
