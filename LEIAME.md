# Plano de estudo C-PRO I — estudos.barukstore.com.br

App de um arquivo só (index.html) + Firebase Auth (Google) + Firestore, hospedado no GitHub Pages.

## 1. Firebase
1. console.firebase.google.com → criar projeto novo (ex.: `estudos-cpro`). Analytics pode desligar.
2. Build → Authentication → Get started → Sign-in method → **Google** → ativar.
3. Authentication → Settings → **Authorized domains** → adicionar `estudos.barukstore.com.br`.
4. Build → Firestore Database → Create database → região `southamerica-east1` (São Paulo) → modo produção.
5. Firestore → aba **Rules** → colar o conteúdo de `firestore.rules` (com os e-mails reais) → Publish.
6. Configurações do projeto → Seus apps → adicionar app **Web** → copiar o objeto `firebaseConfig`.

## 2. Preencher o index.html
No topo do `<script type="module">`:
- `FIREBASE_CONFIG`: colar o objeto do passo 6.
- `ACESSOS`: e-mail Google da Thaís → "thais", da Roberta → "roberta".
- `ADMINS`: seu e-mail (vê e edita os dois planos).

Os e-mails precisam ser **iguais** no index.html e no firestore.rules, em minúsculo.
O index.html só decide o que mostrar; quem bloqueia de verdade é o firestore.rules.

## 3. GitHub Pages
1. Repo novo `vitorrix/estudos` com todos os arquivos desta pasta (o `CNAME` já aponta pro subdomínio).
2. Settings → Pages → Deploy from branch → `main` / root.
3. Registro.br → DNS de barukstore.com.br → CNAME `estudos` → `vitorrix.github.io`.
4. Quando o certificado sair, marcar **Enforce HTTPS** no Pages.

## 4. No celular delas
Abrir https://estudos.barukstore.com.br → Entrar com Google → responder o cartão.
- iPhone: Safari → Compartilhar → Adicionar à Tela de Início.
- Android: Chrome → menu → Adicionar à tela inicial.

## Estrutura dos dados
Firestore: `perfis/thais` e `perfis/roberta`, cada um com `{ answers, progress, savedAt }`.
Pra zerar o plano de alguém, apague o documento dela no console.
