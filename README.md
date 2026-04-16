# Ambiente Local - Laragon + WampServer
[![Status](https://img.shields.io/badge/status-concluído-brightgreen)]()

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
- [ ] Testar `Get-NetTCPConnection`
- [ ] Testar `curl`

## Solução

Alterada a porta...

---

## Testes menos agressivos

*Em desenvolvimento – serão incluídos na v2.0*

- [ ] Parar serviço com `Stop-Service -Name wampapache64 -Confirm`
- [ ] Executar rollback da configuração (voltar para porta 80)
- [ ] Testar `Get-NetTCPConnection -LocalPort 80`
- [ ] Testar `curl http://localhost`

## Segurança aplicada

*Em desenvolvimento – serão incluídos na v2.0*

- Backup do `httpd.conf` antes de qualquer alteração
- Uso de `Stop-Service` em vez de `taskkill /f`
- Verificação pós-alteração com `curl` ou `Invoke-WebRequest`

## Comandos úteis para troubleshooting

| Comando | Finalidade |
|---------|------------|
| `netstat -ab \| findstr :80` | Identificar processo na porta 80 |
| `Get-NetTCPConnection -LocalPort 80` | (v2.0) Filtro TCP com PowerShell |
| `curl http://localhost` | (v2.0) Testar resposta do servidor |

## Documentação completa
[Clique aqui para o PDF](./Documentação%20técnica%20de%20Network%20Troubleshooting.pdf)

## Autor
Rander Caillaud

## Licença
MIT
