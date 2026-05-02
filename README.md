# Ambiente Local - Laragon + WampServer
[![Status](https://img.shields.io/badge/status-concluído-brightgreen)]()
[![Windows](https://img.shields.io/badge/Windows-11-blue)]()
[![PowerShell](https://img.shields.io/badge/PowerShell-7.5.4-blue)]()

## 📌 Índice
- [Sobre o problema](#sobre-o-problema)
- [Ambiente](#ambiente)
- [Diagnóstico](#diagnóstico)
- [Solução](#solução)
- [Documentação completa](#documentação-completa)
- [Autor](#autor)
- [Licença](#licença)

## Sobre o problema
Conflito de porta 80 entre Laragon e WampServer no Windows 11.

## Ambiente

| Componente | Versão |
|------------|--------|
| Windows 11 | 22H2   |
| Laragon    | 8.6.1  |
| WampServer | 3.4.0  |
| PowerShell | 7.5.4  |

## Diagnóstico

Comando usado:

```powershell
netstat -ab | findstr :80
```

*O comando exige privilégios de administrador.*

- [x] Testado com `netstat -ab`
- [x] Testar `Get-NetTCPConnection`
- [x] Testar `curl`

## Solução

Alterada a porta do Apache para 8081 e MySQL para 3308 no Laragon para evitar conflito como o WampServer

---

## Testes menos agressivos

*Boas práticas aplicadas*

- [x] Parar serviço com `Stop-Service -Name wampapache64 -Confirm`
- [x] Executar rollback da configuração (voltar para porta 80)
- [x] Testar `Get-NetTCPConnection -LocalPort 80`
- [x] Testar `curl http://localhost`

## Segurança aplicada

- Backup do `httpd.conf` antes de qualquer alteração
- Uso de `Stop-Service` em vez de `taskkill /f`
- Verificação pós-alteração com `curl` ou `Invoke-WebRequest`

## Comandos úteis para troubleshooting

| Comando | Finalidade |
|---------|------------|
| `netstat -ab \| findstr :80` | Identificar processo na porta 80 |
| `Get-NetTCPConnection -LocalPort 80` | (v2.0) Filtro TCP com PowerShell |
| `curl http://localhost` | (v2.0) Testar resposta do servidor |

## Documentacao completa
[Clique aqui para o PDF V1](./Documentação%20técnica%20de%20Network%20Troubleshooting.pdf) |
[Clique aqui para o PDF V2](https://github.com/RanderCaillaud/ambiente-local-lab/blob/main/network_troubleshooting_v2_final.pdf)

## Autor
Rander Caillaud Pereira Guimarães
Assistente Administrativo | Suporte Técnico Júnior
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/randercaillaud/) | 
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/RanderCaillaud)

## Licença
[License MIT](https://github.com/RanderCaillaud/ambiente-local-lab/blob/main/LICENSE)

---
💡 **Sugestões e feedbacks são bem-vindos!**  
Se você encontrou um bug ou tem uma ideia para a v2.0, sinta-se à vontade para abrir uma [Issue](https://github.com/RanderCaillaud/ambiente-local-lab/issues).

