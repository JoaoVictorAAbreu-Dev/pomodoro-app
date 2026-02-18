# Pomodoro PWA

App Pomodoro com instalacao como aplicativo no desktop/celular, cache offline e persistencia de estado.

## Rodar localmente

PWA precisa de servidor HTTP (nao funciona abrindo o arquivo direto no navegador).

### Opcao A: Python
```bash
python -m http.server 8080
```

### Opcao B: Node.js
```bash
npx serve .
```

Abra em `http://localhost:8080` (ou porta indicada).

## Instalar como app

1. Abra no Chrome/Edge.
2. Clique em `Instalar App` (botao interno) ou no icone de instalacao da barra.
3. Confirme a instalacao.

## Recursos

- Modos Pomodoro, Pausa curta e Pausa longa
- Troca automatica de modo (pausa longa a cada 4 sessoes)
- Notificacoes desktop ao final
- Alarme sonoro opcional
- Persistencia no `localStorage` (duracoes, sessao, progresso)
- Atalhos de teclado:
  - `Espaco`: iniciar/pausar
  - `R`: reiniciar timer
- Funciona offline apos primeiro carregamento

## Estrutura

```text
index.html      # UI + logica do timer
manifest.json   # metadados do PWA
sw.js           # cache e estrategia offline
icons/
  icon-192.png
  icon-512.png
```
