## ports being listened on

```bash
sudo lsof -iTCP -sTCP:LISTEN | grep <program>
```
