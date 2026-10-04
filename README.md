# Central Handem

App de conteúdo do @handemisabella: post do dia, calendário com status, dia de gravação com roteiro, checklist de quem filma nos dias ao vivo, Stories e banco de ideias. Sincroniza entre aparelhos pelo Firebase.

## Arquivos

```
index.html             o app inteiro
firebase-config.js     onde você cola a configuração do Firebase
firestore.rules        regras de acesso (quem pode ver e editar)
manifest.webmanifest   nome, cor e ícone do app na tela inicial
sw.js                  faz o app abrir sem internet
icon-192.png, icon-512.png, apple-touch-icon.png   ícones
```

## 1. Firebase (sincronizar entre aparelhos) · 10 min

1. Entre em **console.firebase.google.com** → **Adicionar projeto** → nome `central-handem`. Pode desligar o Google Analytics.
2. **Criação → Firestore Database → Criar banco de dados.** Local: `southamerica-east1 (São Paulo)`. Modo: **produção**.
3. Na aba **Regras** do Firestore, apague tudo, cole o conteúdo de `firestore.rules` e clique em **Publicar**.
4. **Criação → Authentication → Vamos começar → Anônimo → Ativar.** Não precisa criar usuário nem senha: o app entra sozinho.
5. **Configurações do projeto** (engrenagem) → **Seus apps** → ícone **</>** (Web) → apelido `central` → **Registrar app**. Copie o bloco `firebaseConfig`.
6. Abra `firebase-config.js` e troque `window.FIREBASE_CONFIG = null;` pelo bloco copiado (veja o exemplo no próprio arquivo).
7. Depois de publicar no GitHub: **Authentication → Configurações → Domínios autorizados** → adicione `SEU-USUARIO.github.io`.

Os dados de configuração podem ficar públicos no GitHub. As regras só deixam o próprio app gravar, e só no formato certo.

## 2. GitHub Pages · 5 min

1. Crie um repositório (ex.: `central-handem`).
2. **Add file → Upload files**: envie todos os arquivos desta pasta. **Commit changes.**
3. **Settings → Pages** → Branch `main`, pasta `/ (root)` → **Save**.
4. Em 1–2 minutos o endereço aparece: `https://SEU-USUARIO.github.io/central-handem/`.

## 3. Tela inicial

- **iPhone:** abra no Safari → Compartilhar → **Adicionar à Tela de Início**.
- **Android:** abra no Chrome → menu ⋮ → **Instalar app**.

Mande o mesmo endereço para quem filma com você. Ela abre, marca o checklist dos dias ao vivo e você vê na hora.

## Sem internet

O app abre e deixa marcar mesmo offline. Quando a internet volta, sincroniza sozinho.

## Atualizar o calendário

O conteúdo fica no começo do `<script>` do `index.html` (listas `ITEMS`, `SESSIONS`, `CAPDAYS`, `TEMPLATES`, `AGENDA`, `TEATRO`). Edite e envie de novo pelo GitHub. A cada atualização, troque a versão em `sw.js` (`central-handem-v4` → `v5`, e assim por diante) para os celulares pegarem a versão nova.
