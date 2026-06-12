# Trabalho Prático CI/CD
disponível em: https://maria.qa


## Execução Local via Docker

```bash
sudo docker compose up
```

Simplifica um pouco a execução local de forma reproduzível.
por baixo dos panos, ele faz:
  - bind da porta 8080 do host com 8080 do container
  - bind da pasta ui/ do host com a app/ de dentro do container, para permitir o hot reload
  - instalação das dependências com npi ci (clean install), que é melhor para containers, pois instala sem de forma mais rápida e sem alterar o package-lock
  - expõe a porta 8080, por convenção
  - inicia o servidor de dev na porta 8080

## Proteção da main
Para garantir a integridade da main, o seguinte ruleset foi configurado:

  - Nenhum grupo de bypass
  - Restrict Deletions (main não pode ser apagada)
  - Require a pull request before merging (impede pushes diretos na main)
  - Require status checks to pass (utiliza a action lint)
  - Block force pushes

prints em prints/