# 🖥️ Ambiente Local de Desenvolvimento – Laragon + WampServer no Windows 11

[![Status](https://img.shields.io/badge/status-concluído-brightgreen)]()
[![Windows](https://img.shields.io/badge/Windows-11-blue)]()
[![PowerShell](https://img.shields.io/badge/PowerShell-7.5.4-blue)]()

## Sobre o problema

Ao tentar rodar **Laragon** e **WampServer** simultaneamente no Windows 11, ambos tentam usar as mesmas portas padrão:
- **Apache** → porta 80
- **MySQL** → porta 3306

Isso gera conflitos. Este repositório documenta o diagnóstico e a resolução.

## Ambiente utilizado

| Componente | Versão |
|------------|--------|
| Sistema operacional | Windows 11 |
| Laragon | 8.6.1 |
| WampServer | 3.4.0 |
| PowerShell | 7.5.4 |

## Diagnóstico (o que já foi testado)

Para verificar qual processo está usando a porta 80:

```powershell
netstat -ab | findstr :80
