# RTLC^2

This is the lightweight submission release of RTLC^2. It keeps the core multi-module RTL code completion pipeline, including hybrid retrieval, completion-oriented prompt construction, and selective iteration guided by generation signals, while omitting large bundled retrieval assets to keep the release small.

## What Is Included

- `src/`: core completion system modules
- `prompts/`: public prompt assets
- `config/`: configuration placeholders for public use
- `RTL-Repo/`: placeholder location for the external retrieval corpus
- `archive/json/retrieval_cache/`: placeholder location for the external retrieval cache

## Lightweight Release Note

This submission release omits the bundled external RTL-Repo corpus and retrieval cache included in the full internal workflow. The directory structure is kept so that users can later add these assets manually if needed.

## Environment

RTLC^2 is intended to run on Linux with Python 3.10.

Before running the full system, prepare the following:

- Python 3.10 environment
- dependencies from `requirements.txt`
- access to a completion backend, configured through environment variables when needed
- optional external retrieval assets placed under `RTL-Repo/` and `archive/json/retrieval_cache/`

If you use an API backend, set:

- `RTLC2_API_BASE`
- `RTLC2_API_KEY`

If you use a local backend, set:

- `RTLC2_LOCAL_MODEL_PATH`

## Installation

Install Python dependencies from `requirements.txt`.

Typical packages include:

- `transformers`
- `datasets`
- `rank_bm25`
- `fuzzywuzzy`
- `python-Levenshtein`

## Usage

This lightweight release is intended to be paired with the lightweight Realbench-Comp release, which provides the public black-box request construction and evaluation scripts.

In the paired setup:

1. Realbench-Comp-Lite builds a normalized completion request from a masked RTL target.
2. The RTLC^2 adapter invokes the completion pipeline in this repository.
3. Realbench-Comp-Lite evaluates the returned completion under text-level and functional metrics.

## Interface

Input:
- a request object containing target prefix, target suffix, and cross-file context files

Output:
- completion-only Verilog text

## License

See `LICENSE`.
