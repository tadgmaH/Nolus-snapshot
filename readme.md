# Nolus Protocol (nolus-rila)
## Snapshot


> Snapshot parameters: Pruning - nothing, Indexer - kv, Size - 20G

Install dependencies
```
sudo apt-get update
sudo apt-get install gzip tar

```
Stop service and reset data
```
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```

Download snapshot and restore priv_validator_state.json
```
curl -sSL http://135.181.160.61/backups/snapshot_nolus.tar.gz | tar xz -C $HOME/.nolus
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json 
```

Restart service and check logs
```
sudo systemctl start nolusd
sudo journalctl -u nolusd -f --no-hostname -o cat
```
