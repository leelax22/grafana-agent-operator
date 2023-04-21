# prometheus 배포
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

values-prometheus.yaml 수정사항
- service를 LoadBalancer로 변경
- remote write 활성화
- 암호화를 위해서 web_config 파일 추가
- 프로브 또한 엔드포인트로 접근하기때문에 probeHeader를 설정, 설정하지 않으면 인증 에러로 prometheus pod가 error 상태가 지속됨
- web_config.yml에는 bcrypt 암호화, Header에는 base64 암호화로 작성
```
server:
  extraFlags:
    - web.enable-remote-write-receiver

  extraArgs:
    web.config.file: /etc/config/web_config.yml
    
  probeHeaders:
  - name: Authorization
    value: Basic emVuaXRoOndwc2x0bXFscWpTMUA=

serverFiles:
  web_config.yml:
    basic_auth_users:
      user: 'bcrypt password'
```

```
helm install -f values-prometheus.yaml prometheus prometheus-community/prometheus
```

# loki 배포

# grafana 배포

# grafana-agent-operator 배포

# grafana-agent 배포

# grafana
