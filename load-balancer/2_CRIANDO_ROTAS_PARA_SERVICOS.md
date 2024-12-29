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
