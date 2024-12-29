## Criando o balanceador de carga

```bash
PROFILE=nome_do_perfil
COMPARTMENT=ocid_do_compartimento
NAME=nome_do_balanceador
SHAPE_SIZE=tamanho_do_shape | Fixed shapes - 10Mbps, 100Mbps, 400Mbps, 8000Mbps would be deprecated and only shape       allowed would be `Flexible

cat << EOT >> /tmp/subnets-ids.json
[
  "ocid_da_subnet", "quantas_ocids_desejar_no_array"
]
EOT
oci lb load-balancer create --profile $PROFILE --compartment-id $COMPARTMENT --display-name $NAME  --subnets-ids file:///tmp/subnets-ids.json --shape-name $SHAPE_SIZE
```

## Listando balanceadores de carga

```bash
PROFILE=nome_do_perfil
COMPARTMENT=ocid_do_compartimento

oci lb load-balancer list --profile $PROFILE --compartment-id $COMPARTMENT
```
## Obtendo apenas balanceador de carga pelo OCID (id do recurso)

```bash
PROFILE=nome_do_perfil
LB_OCID=ocid_do_balanceador_de_carga

oci lb load-balancer get --profile $PROFILE --load-balancer-id $LB_OCID
```
