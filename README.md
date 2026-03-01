# Pomodoro PWA

Aplicação web baseada na técnica Pomodoro para gerenciamento de foco e produtividade. Desenvolvida como Progressive Web App (PWA), permite instalação no dispositivo e funcionamento offline.

## Funcionalidades

**Temporizador**
- Ciclos configuráveis de Pomodoro, pausa curta e pausa longa
- Anel de progresso animado com marcações de tempo
- Alternância automática entre foco e pausa (auto-avançar)
- Indicador de sessão e pontos de progresso do ciclo
- Alarme sonoro ao fim de cada sessão
- Notificações do sistema (com permissão)
- Atalhos de teclado: `Espaço` inicia/pausa · `R` reinicia · `M` abre rádio

**Estatísticas**
- Gráfico de barras de sessões por dia (últimos 7 ou 30 dias)
- KPIs: sessões hoje, total histórico e horas de foco acumuladas
- Streak de dias consecutivos de uso
- Histórico persistido no `localStorage`

**Rádio ambiente** — via [Radio Browser API](https://www.radio-browser.info/)
- Busca por gênero ou nome de estação (lofi, jazz, ambient...)
- Reprodução direta no app com controle de volume
- Gratuito, sem necessidade de cadastro ou chave de API

**Clima** — via [Open-Meteo](https://open-meteo.com/)
- Temperatura e condição climática atual exibidas no header
- Detecta a localização do dispositivo automaticamente
- Gratuito, sem necessidade de cadastro ou chave de API

**Notion** — via [Notion API](https://developers.notion.com/)
- Envia um resumo diário para uma página do Notion com sessões, tempo de foco e streak
- Token e Page ID configurados pelo próprio usuário e salvos localmente

**PWA**
- Instalável em desktop e mobile via manifest
- Service Worker com cache-first para assets e network-first para fontes
- Funciona offline após o primeiro acesso

## Tecnologias

<p align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" width="50" height="50" alt="HTML5"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" width="50" height="50" alt="CSS3"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" width="50" height="50" alt="JavaScript"/>
</p>

- **HTML5** — Estrutura e semântica
- **CSS3** — Estilização, variáveis CSS e animações
- **JavaScript (ES6+)** — Lógica do temporizador, APIs e manipulação do DOM
- **Web Audio API** — Geração do alarme sonoro
- **Service Worker** — Cache e suporte offline
- **Geolocation API** — Localização para o widget de clima

## APIs Externas

| API | Uso | Autenticação |
|-----|-----|--------------|
| [Open-Meteo](https://open-meteo.com/) | Clima atual | Nenhuma |
| [Radio Browser](https://www.radio-browser.info/) | Estações de rádio | Nenhuma |
| [Notion API](https://developers.notion.com/) | Resumo diário | Token próprio |

## Estrutura do Projeto

```
pomodoro-pwa/
│
├── index.html       # App completo (HTML + CSS + JS em arquivo único)
├── manifest.json    # Configuração PWA
├── sw.js            # Service Worker
└── icons/
    ├── icon-192.png
    └── icon-512.png
```

## Como Executar Localmente

Clone o repositório:

```bash
git clone https://github.com/SEU_USUARIO/pomodoro-pwa.git
cd pomodoro-pwa
```

Execute com Live Server (VS Code), qualquer servidor HTTP local, ou:

```bash
npx serve .
```

> O Service Worker e a Geolocation API requerem HTTPS ou `localhost` para funcionar corretamente.

## Configurar o Notion (opcional)

1. Acesse [notion.so/my-integrations](https://www.notion.so/my-integrations) e crie uma nova integration
2. Copie o **Integration Token** (`secret_...`)
3. Abra a página do Notion onde quer salvar os resumos
4. Clique em `···` → **Connections** → conecte sua integration
5. Copie o **Page ID** da URL da página (os 32 caracteres após o último `/`)
6. Cole o token e o ID no painel Notion dentro do app e clique em **Salvar configuração**

## Publicar com GitHub Pages

Após fazer push para o repositório, vá em **Settings → Pages → Source: Deploy from branch → `main` → `/root`** e salve. O app ficará disponível em:

```
https://SEU_USUARIO.github.io/pomodoro-pwa
```