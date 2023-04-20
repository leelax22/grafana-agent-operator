# prometheus 배포
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

values-prometheus.yaml 수정사항
- service를 LoadBalancer로 변경
- 암호화를 위해서 추가
```
server:
  extraArgs:
    web.config.file: /etc/config/web_config.yml
serverFiles:
  web.config.yml:
    basic_auth_users:
      user: 'bcrypt password'
```




# loki 배포

# grafana 배포

# grafana-agent-operator 배포

# grafana-agent 배포

# grafana
