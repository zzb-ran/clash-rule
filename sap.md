1.login 
US AWS: https://api.cf.us10-001.hana.ondemand.com
SG Azure: https://api.cf.ap21.hana.ondemand.com
cf login -a ADDRESS

2.pull
无CF TUNNEL
1. cf push APP_NAME --docker-image uncleluo/mous:latest -m 512M --health-check-type port
2. cf set-env APP_NAME APP_UUID YOUR_UUID
3. cf restage APP_NAME
4. cf logs APP_NAME --recent

有CF TUNNEL
1. cf push APP_NAME --docker-image ghcr.io/uncleluogithub/sapcf:latest -m 512M -k 512M --health-check-type port --no-route --no-start
2. cf set-env APP_NAME APP_UUID YOUR_UUID
3. cf set-env APP_NAME VMESS_HOST TUNNEL_ADDRESS
4. cf set-env APP_NAME TUNNEL_TOKEN TUNNEL_TOKEN
5. cf start APP_NAME
6. cf logs APP_NAME --recent
