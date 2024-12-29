## Criando o balanceador de carga

```bash
PROFILE=nome_do_perfil
COMPARTMENT=ocid_do_compartimento
NAME=nome_do_balanceador

cat << EOT >> /tmp/subnets-ids.json
[
  "ocid_da_subnet", "quantas_ocids_desejar_no_array"
]
EOT
oci lb load-balancer create --profile $PROFILE --compartment-id $COMPARTMENT --display-name $NAME  --subnets-ids file:///tmp/subnets-ids.json
```
