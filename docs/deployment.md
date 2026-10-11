# Manual Deployment M03

## Application Path
`/srv/cc-m03`

## Service
`cc-m03.service`

## Backend
`127.0.0.1:8000`

## Public Endpoint
`http://<PUBLIC_IP>/`

## Update Procedure

```bash
cd /srv/cc-m03
git pull
source .venv/bin/activate
python -m pip install -r requirements.txt
sudo systemctl restart cc-m03
sudo systemctl status cc-m03 --no-pager
curl -fsS http://127.0.0.1:8000/health
curl -fsS http://127.0.0.1/health
