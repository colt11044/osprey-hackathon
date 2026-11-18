# Security and project status

This repository preserves a hackathon prototype. The hardware has been disassembled; no Osprey service or network connection is active. The operational coordinator is not hardened for deployment.

Two access-control gaps remain in the archived code:

- `scripts/run_pi.sh` starts the coordinator on `0.0.0.0:8000`. The state, image, command, and WebSocket endpoints in `src/osprey/app.py` do not authenticate clients. Anyone able to reach that server could read incident data or issue coordinator commands.
- The quick public tunnel and `/ws/scout` accept scout connections without authentication. If that tunnel were started, an untrusted client could submit false scout imagery or state.

Do not connect this version to a public network or real hardware for operational use. Add authentication, authorization, transport controls, and deployment-specific review before reuse. The browser simulation in `simulation/` is a separate scripted concept demonstration with no live hardware connection.
