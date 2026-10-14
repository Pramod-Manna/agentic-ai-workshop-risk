# Setup: Risks, incidents and problems (RISK)

## Open your notebook

Use a Google account and open [Google Colab](https://colab.research.google.com/). Choose **Open notebook → Upload** and upload one notebook from this folder. After publication, you can also use the GitHub tab in Colab to find the repository. Save a working copy to your own Drive.

- `starter_RISK_no_neo4j.ipynb`: uses supplied Python lookup tables; no database account required.
- `starter_RISK.ipynb`: connects to a Neo4j database.

Run the installation cell and then the embedding-model cell. The model downloads on first use. Both notebooks already contain the RISK records and public question pack.

## Configure your LLM

1. Obtain an API key from your chosen LLM provider.
2. In Colab Secrets (the key icon), add `LLM_API_KEY` and enable notebook access.
3. In **Your LLM provider**, set `LLM_MODEL` to a model your account can access. Set `LLM_BASE_URL` if using an OpenAI-compatible endpoint from another provider.
4. If your provider requires its own SDK, adapt `call_llm(prompt)` to return a plain reply string. Install that SDK in the setup cell. Use `temperature=0` where supported to reduce variation.
5. Run the LLM check before continuing. A full public run makes roughly 25 LLM calls; availability and quotas depend on your provider.

The supplied model name is a configurable example. Keep your key out of cells and outputs. No LLM key is provided by this repository.

## Neo4j version only

Create or use a Neo4j Aura instance via [Neo4j Aura](https://neo4j.com/cloud/aura/), then add these Colab Secrets with notebook access enabled:

| Secret | Value |
| --- | --- |
| `NEO4J_URI` | Connection URI from your instance |
| `NEO4J_USER` | Database username |
| `NEO4J_PASSWORD` | Database password |

Run the connection cell and confirm `Connection successful`. Use a dedicated workshop database: the supplied graph-building cell clears its existing graph before rebuilding it. If connecting is difficult, switch to `starter_RISK_no_neo4j.ipynb`; its lookup tables and traversal are already supplied.

## Work and submit

Follow the tasks in [README.md](README.md). Re-run graph construction whenever you change `PATTERNS`, then run the public questions and fill the outcomes. Complete one notebook, restart the runtime and run all, then submit the completed notebook.

## Troubleshooting

| Issue | Check |
| --- | --- |
| Missing package | Re-run the installation cell; restart and run all if needed. |
| Model download stalls | Check connectivity and retry the embedding cell. |
| Secret missing | Confirm the exact secret name and notebook-access toggle. |
| LLM authentication/model error | Check your key, `LLM_MODEL` and `LLM_BASE_URL`. |
| Rate or quota limit | Check your provider's quota and retry when available. |
| Neo4j connection fails | Check credentials, instance status and reconnect. The no-Neo4j notebook is an alternative. |
| Registry changes have no effect | Re-run section 7 before the public question pack. |

These instructions target Colab. Local Jupyter users need the notebook packages installed and the same secret names supplied through environment variables or a private `.env` file.
