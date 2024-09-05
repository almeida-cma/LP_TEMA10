# LP_TEMA10
FE-BE
# esc-leads
Simulação de escritório de projetos com Leads
<br>
Leads - aprimoramento - Escritório
<br>
npm init -y
<br>
npm install express body-parser sqlite3 bcryptjs express-session path
<br>
Para subir servidor executar:
<br>
node server.js
------------------------------------------------------------
Sobre o Firebase, utilizar o seguinte código como regra:
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {

    // Regras para a coleção de eventos
    match /eventos/{eventoId} {
      allow read, write: if request.auth != null && request.auth.uid == resource.data.usuarioId;
    }

    // Regras para a coleção de orçamentos
    match /orcamentos/{orcamentoId} {
      allow read, write: if request.auth != null && request.auth.uid == resource.data.usuarioId;

      // Regras para a subcoleção itens dentro de orçamentos
      match /itens/{itemId} {
        allow read, write: if request.auth != null && request.auth.uid == resource.data.usuarioId;
      }
    }

    // Regra geral para outros documentos (apenas usuários autenticados)
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}

