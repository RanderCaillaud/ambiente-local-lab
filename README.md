# Ambiente Local - Laragon + WampServer

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

## Solução
Alterada a porta do Apache no WampServer para 8080.  
Detalhes no PDF abaixo.

## Documentação completa
[Clique aqui para o PDF](./Documentação%20técnica%20de%20Network%20Troubleshooting.pdf)

## Autor
Rander Caillaud

## Licença
MIT
