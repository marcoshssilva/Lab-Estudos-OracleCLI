# Adicionando escutador de porta para conjunto de serviços

```bash
oci lb listener create \
  --profile $PROFILE \
  --default-backend-set-name $BACKENDSET_NAME \   ## nome do conjunto de serviços
  --load-balancer-id $LB_OCID \                   ## ocid do balanceador de carga
  --name $LISTENER_NAME \                         ## nome do seu listener (inventa um aqui)
  --port $PORT \                                  ## porta de acesso público para redirecionamento dos serviços
  --protocol $PROCOCOL                            ## procoloco de rede (TCP, HTTP, HTTP2, GRCP ou etc...)
```
