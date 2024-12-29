## Criando um conjunto de serviços para balanceamento

> Exemplo para TCP simples
```bash
PROFILE=nome_do_perfil
HEALTH_CHECK_PROTOCOL=procolo_de_rede | Aceitos TCP ou HTTP
LB_OCID=voce_ja_sabe_que_eh_o_ocid_do_recurso
NAME=nome_do_conjunto_de_servicos
POLICY=tipo_de_regra_de_distribuicao_de_balanceamento | Aceitos ROUND_ROBIN, IP_HASH e LEAST_CONNECTIONS

oci lb backend-set create --profile $PROFILE --health-checker-protocol $HEALTH_CHECK_PROTOCOL --load-balancer-id $LB_OCID --name $NAME --policy $POLICY
```

> Exemplo para HTTP proxy como NGINX
```bash
oci lb backend-set create \
  --profile $PROFILE \                    ## nome do perfil
  --health-checker-protocol HTTP \        ## protocolo do serviço
  --health-checker-port 32686 \           ## porta do serviço
  --health-checker-url-path /healthz \    ## caminho do recurso
  --health-checker-return-code 200 \      ## código de status esperado do teste de verificacao
  --health-checker-retries 3 \            ## quantidade de tentativas a verificacao de disponibilidade do serviço
  --health-checker-interval-in-ms 10000 \ ## intervalo entre chamadas a verificacao de disponibilidade do serviço
  --health-checker-timeout-in-ms 3000 \   ## tempo em milisegundos aguarandando resposta do serviço
  --load-balancer-id $OCID_LOADBALANCER \
  --name $NAME \
  --policy $POLICY
```

## Adicionando serviços ao conjunto de balanceamento

```bash
PROFILE=nome_do_perfil
NAME=nome_do_conjunto_de_servicos_criado_anteriormente
SERVICE_IP=ip_do_servico_alvo
PORT=porta_do_servico_alvo
OCID_LOADBALANCER=voce_ja_sabe_que_eh_o_ocid_do_recurso

oci lb backend create \
  --profile $PROFILE \
  --backend-set-name $NAME \
  --ip-address $SERVICE_IP \
  --load-balancer-ip $OCID_LOADBALANCER \
  --port $PORT
```
