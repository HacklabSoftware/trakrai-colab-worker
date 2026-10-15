# TrakrAI GPU worker for Google Colab

Lend a Google Colab GPU to your factory's model training in [TrakrAI](https://ai.trakr.live).

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HacklabSoftware/trakrai-colab-worker/blob/main/trakrai-colab-worker.ipynb)

## How it works

1. In TrakrAI, open **Model training → Compute** and click **Connect a Colab GPU** (or pick **Start a Colab GPU for this job only** in a job's GPU worker list). TrakrAI shows a pairing code.
2. Click the badge above. Colab opens the notebook and asks for a T4 GPU.
3. Paste the code into the notebook's `PAIRING_CODE` field and choose **Runtime → Run all**. The cell connects by itself.

A pairing code works once and expires after 15 minutes; create a new one in TrakrAI if it has expired. The worker runs only jobs for the factory the code was created for, and stops when you stop the notebook. A code created for a single job runs that job, then stops and releases the Colab runtime. It uses your own Colab compute units; TrakrAI never sees your Google account.

## Requirements

- A Colab account with a paid plan or a positive compute-unit balance. Colab's terms do not allow background workers on the free tier.
- A pairing code from TrakrAI, created by someone with model-admin access to the factory.

## What the notebook does

The single code cell exchanges the pairing code for a worker token, downloads the worker code from your TrakrAI site, and runs it on the Colab GPU until you stop the cell. Nothing is installed outside the Colab runtime, and the token is stored only in the runtime's temporary disk.
