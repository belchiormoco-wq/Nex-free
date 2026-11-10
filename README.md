# UNITEL ZERO-RATED LAB — Android starter

Versão inicial nativa para Android. Inclui:
- Dashboard simples;
- edição de host e portas;
- teste TCP independente;
- teste TLS com validação padrão de certificados Android;
- logs locais de diagnóstico;
- workflow GitHub Actions para gerar APK debug.

## Limites importantes

Este projeto **não**:
- contorna tarifários ou cobrança da Unitel;
- implementa Sponsored Data;
- estabelece ainda um túnel SSH;
- implementa ainda `VpnService`/TUN;
- garante que o host FreeVPN aceite TLS na porta 443.

A isenção de dados exige acordo e configuração técnica oficial da operadora. Use apenas servidores e contas para os quais tenha autorização.

## Build no GitHub Actions

1. Crie um repositório GitHub vazio.
2. Envie todos os ficheiros desta pasta para a raiz do repositório.
3. Abra o separador **Actions**.
4. Se necessário, aceite a ativação de workflows.
5. Execute **Build Android APK** com **Run workflow**, ou faça push para `main`.
6. Abra a execução concluída e descarregue o artefacto `UNITEL-ZERO-RATED-debug`.
7. Extraia o ZIP do artefacto e instale `app-debug.apk` no Android.

## Configuração inicial

A aplicação abre com:
- Host: `ssh-us-1.vpnv.cc`
- TLS: `443`
- TCP/SSH: `444`

Os testes TCP e TLS são separados. Um teste TCP bem-sucedido na porta 444 **não** prova autenticação SSH. Um handshake TLS bem-sucedido na porta 443 **não** prova que o servidor encaminha TLS para SSH.

## Segurança

- Não coloque passwords, tokens ou chaves privadas no código, GitHub ou APK.
- Altere a password de qualquer conta que tenha sido exposta.
- Não desative a validação TLS para "fazer funcionar".
- O APK gerado pelo workflow é uma build debug, não uma versão de produção assinada.
