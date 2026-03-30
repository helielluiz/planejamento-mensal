# 📅 Planejamento Mensal — PWA

App mobile para controle mensal de horas trabalhadas, receitas e despesas.
Sincroniza em tempo real entre dois celulares via Firebase.

---

## 🚀 Como configurar (passo a passo)

### PASSO 1 — Criar projeto no Firebase

1. Acesse **https://console.firebase.google.com**
2. Clique em **"Adicionar projeto"**
3. Nome do projeto: `planejamento-mensal` (ou qualquer nome)
4. Desative o Google Analytics (não precisa) → clique em **Criar projeto**
5. Aguarde criar e clique em **Continuar**

---

### PASSO 2 — Criar o banco de dados (Firestore)

1. No menu lateral esquerdo, clique em **Firestore Database**
2. Clique em **Criar banco de dados**
3. Selecione **Iniciar no modo de teste** → clique em Avançar
4. Escolha a região `southamerica-east1 (São Paulo)` → clique em **Ativar**

---

### PASSO 3 — Registrar o app Web e pegar as credenciais

1. Na página inicial do projeto, clique no ícone **`</>`** (Web)
2. Apelido do app: `planejamento-web` → clique em **Registrar app**
3. Vai aparecer um bloco de código com `firebaseConfig`. Copie os valores:

```js
const firebaseConfig = {
  apiKey: "AQUI_ESTA_SUA_API_KEY",
  authDomain: "seu-projeto.firebaseapp.com",
  projectId: "seu-projeto",
  appId: "1:123456:web:abcdef"
};
```

4. Clique em **Continuar no console**

---

### PASSO 4 — Subir no GitHub

1. Acesse **https://github.com/new**
2. Nome do repositório: `planejamento-mensal`
3. Deixe **Público** → clique em **Create repository**
4. Na próxima tela, clique em **"uploading an existing file"**
5. Arraste todos os arquivos desta pasta para a página
6. Clique em **Commit changes**

---

### PASSO 5 — Ativar GitHub Pages

1. No seu repositório, clique em **Settings** (aba superior)
2. No menu lateral, clique em **Pages**
3. Em "Source", selecione **Deploy from a branch**
4. Branch: **main** / Folder: **/ (root)** → clique em **Save**
5. Aguarde ~2 minutos. Seu app vai estar em:
   ```
   https://SEU_USUARIO.github.io/planejamento-mensal/
   ```

---

### PASSO 6 — Configurar o Firebase no app (primeira vez)

1. Abra o link do GitHub Pages no celular
2. Na tela de configuração, cole os 4 valores do Firebase:
   - `apiKey`
   - `authDomain`
   - `projectId`
   - `appId`
3. Clique em **Salvar e conectar**
4. Repita no celular da sua esposa

---

### PASSO 7 — Instalar como app (ícone na tela inicial)

**Android (Chrome):**
1. Abra o link no Chrome
2. Toque nos 3 pontinhos (menu)
3. Toque em **"Adicionar à tela inicial"**
4. Confirme → vai aparecer o ícone como um app normal

**iPhone (Safari):**
1. Abra o link no Safari
2. Toque no botão de compartilhar (quadrado com seta)
3. Toque em **"Adicionar à Tela de Início"**
4. Confirme

---

## ✅ Pronto!

Os dados sincronizam automaticamente em tempo real.
Quando você lançar uma despesa, sua esposa já vê na hora (e vice-versa).

---

## 💡 Dicas de uso

- O **fator valor/hora** fica salvo no celular (não precisa digitar todo dia)
- Use as **setas** para navegar entre meses — cada mês tem seus próprios dados
- Para remover um item, toque no **×** ao lado

---

## 🔒 Segurança (opcional — após testar)

Após o app funcionando, vá no Firestore → **Regras** e substitua por:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /planejamento/{document} {
      allow read, write: if true;
    }
  }
}
```

Isso já está configurado no modo teste por 30 dias.
Para uso de longo prazo, considere adicionar autenticação.
