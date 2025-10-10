# Workspace Persistence Check (Done before testing session)

**Goal**: Find out what survives stop/start

## Execution summary
- Created markers: /workspace/_persist_probe.txt, ~/home_probe.txt, mysite/_repo_probe.txt.
- Performed Gitpod "Stop" -> "Start" and reconnected via Gateway.

# Expected results: 
- WORKSPACE: OK
- REPO: OK
- HOME: MISSING

# Actual results:
- WORKSPACE: OK
- REPO: OK
- HOME: MISSING

## Terminal commands and Steps

1.
```bash
whoami && pwd
echo "marker $(date)" | tee /workspace/persist_check.txt
mkdir -p /workspace/persist_dir && echo "ok" > /workspace/persist_dir/keep.txt
touch ~/home_marker.txt
touch mysite/persisted_in_repo.txt
ls -la /workspace | head -n 20
ls -la ~ | head -n 20
```

2. In the Gitpod dashboard: Stop the workspace.
3. Start it again, reconnect via Gateway → “Open in PyCharm”.
3. Re-open terminal and run the following for verification:

```bash
ls -la /workspace
ls -la ~
test -f /workspace/persist_check.txt && echo "workspace OK"
test -f ~/home_marker.txt && echo "home OK" || echo "home missing"
test -f mysite/persisted_in_repo.txt && echo "repo file OK"
```
