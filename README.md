# Gridica Node

Gridica Node is a local inference agent designed to operate within the Gridica decentralized inference network. It connects to the Gridica control layer, receives inference jobs, runs them using installed models on local hardware, and securely returns results for verification and reward attribution.

## Overview

Each node runs on a GPU-enabled machine and communicates with the Gridica server using WebSocket (for job coordination and heartbeat) and HTTP (for metadata and config sync). Nodes do not host APIs themselves — they are passive execution units within a distributed job pipeline.

All inference logic is executed locally. Nodes never forward requests to external APIs. Every response is signed and linked to a specific job and model version.

## Responsibilities

- Maintain a persistent WebSocket connection with the orchestrator
- Accept and execute inference jobs using configured model runtimes (e.g., vLLM)
- Handle model installation and validation based on assigned job type
- Submit results and metadata back to the control layer
- Periodically send status heartbeats and resource metrics

## Interaction with Server

The server routes user-facing API requests and selects eligible nodes based on:

- Hardware capacity
- Supported model
- Uptime and response history
- Region (if applicable)

Jobs are sent over WebSocket.

## Requirements

- Linux system with NVIDIA GPU (8GB+ VRAM)
- Python 3.10+ or Docker runtime
- Stable internet connection (WebSocket + HTTP)
- Gridica account Id

## Development Status

This repository is currently in concept and planning phase. MVP node implementation will begin during the Q2 2025 testnet rollout. 

## Resources

- [Project site](https://gridica.network)
- [Overview](https://gridica.gitbook.io/v1)  
- [Node role](https://gridica.gitbook.io/v1/system-architecture/gridica-node)

## License

MIT License
