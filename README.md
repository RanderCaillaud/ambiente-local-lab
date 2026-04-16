# 🖥️ Ambiente Local de Desenvolvimento – Laragon + WampServer no Windows 11

[![Status](https://img.shields.io/badge/status-concluído-brightgreen)]()
[![Windows](https://img.shields.io/badge/Windows-11-blue)]()
[![PowerShell](https://img.shields.io/badge/PowerShell-7.5.4-blue)]()

## 📌 Índice
- [Sobre o problema](#sobre-o-problema)
- [Ambiente utilizado](#ambiente-utilizado)
- [Diagnóstico](#diagnóstico)
- [Solução aplicada](#solução-aplicada)
- [Testes menos agressivos](#testes-menos-agressivos)
- [Segurança aplicada](#segurança-aplicada)
- [Comandos úteis para troubleshooting](#comandos-úteis-para-troubleshooting)
- [Documentação completa (PDF)](#documentação-completa-pdf)
- [Autor](#autor)
- [Licença](#licença)

---

## Sobre o problema

Ao tentar rodar **Laragon** e **WampServer** simultaneamente no Windows 11, ambos tentam usar as mesmas portas padrão:
- **Apache** → porta 80
- **MySQL** → porta 3306

Isso gera conflitos, impedindo que um dos serviços (ou ambos) inicie corretamente. Este repositório documenta o diagnóstico e a resolução desse conflito.

---

## Ambiente utilizado

| Componente | Versão |
|------------|--------|
| Sistema operacional | Windows 11 (atualizado) |
| Laragon | [coloque a versão que você usou] |
| WampServer | [coloque a versão] |
| PowerShell | 7.5.4 |
| Terminal | Windows Terminal (ou PowerShell ISE) |

---

## Diagnóstico

### 1. Verificar qual processo está usando a porta 80

```powershell
# Comando 1 – mostra o PID e o nome do processo (exige admin)
netstat -ab | findstr :80
