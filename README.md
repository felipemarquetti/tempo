# FasTrain — Front-end (mobile + desktop)

Front-end estático (HTML/CSS/JS puro, sem build) que segue a mockup enviada:
splash → login/cadastro → dashboard → trens em trânsito → mapa da rota →
perfil → gestão de frota → sensores → notificações.

## Como abrir
Basta abrir `index.html` no navegador (duplo clique) ou rodar um server local:
```
cd fastrain
python3 -m http.server 8080
```
depois acesse `http://localhost:8080`.

## Estrutura
```
fastrain/
├── index.html        → todas as telas (SPA simples, sem framework)
├── css/style.css      → tokens de cor oficiais + todos os componentes
├── js/icons.js        → ícones SVG inline (sem depender de internet)
├── js/data.js         → dados mockados (trens, sensores, notificações)
├── js/app.js          → navegação entre telas e renderização das listas
└── assets/
    ├── logo-light.png → logo oficial em fundo claro
    └── logo-dark.png  → logo oficial em fundo escuro
```

## Cores oficiais (extraídas da mockup)
| Nome           | Hex       | Uso                                   |
|----------------|-----------|----------------------------------------|
| Vermelho Vivo  | `#c92a2a` | menu lateral, botões, cards de destaque |
| Cinza Escuro   | `#404040` | telas escuras, pills de navegação      |
| Cinza          | `#5b5b5b` | painéis internos (dashboard, perfil)   |
| Branco         | `#ffffff` | telas claras, cards de sensores         |

Como havia duas versões (clara/escura) de cada tela na mockup, optei por
**alternar o tema a cada tela** dentro do fluxo, mantendo o menu vermelho fixo
em todas — assim o sistema usa as duas variantes de forma consistente, sem
misturar as duas na mesma tela.

## Responsivo
- **Mobile (< 900px):** menu hambúrguer abre o sidebar vermelho por cima do conteúdo.
- **Desktop (≥ 900px):** sidebar vermelho fixo à esquerda, igual à mockup desktop.

## O que já funciona
- Navegação completa entre todas as telas da mockup.
- Toggle **List / Maps** na tela de trens em trânsito.
- Clique no ID do trem abre o mapa de rota detalhado.
- Mostrar/ocultar senha nos formulários.
- Listas de trens, sensores e notificações renderizadas a partir de `js/data.js`
  (fácil de trocar por dados reais quando o back-end existir).

## Próximos passos (quando entrarmos no back-end)
- Trocar `js/data.js` por chamadas fetch/API.
- Validar formulários (login, cadastro) e mostrar erros reais.
- Autenticação de verdade (hoje os botões "Enter"/"Create account" só navegam).
