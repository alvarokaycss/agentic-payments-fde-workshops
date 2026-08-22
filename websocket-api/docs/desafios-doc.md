## Solução Implementada - Desafio 1

**Critério de conclusão:** abrir 3 abas com nomes diferentes e ver a lista de online atualizar
em tempo real em todas elas, tanto ao entrar quanto ao sair.

**Solução implementada para conclusão:**
- Criado o evento `presence` para avisar em tempo real quem está conectado (ao entrar e ao sair).
- Adicionado `userId` no `join` e no `chat` para diferenciar mensagens mesmo se houver usuários com o mesmo nome.
- Contador de usuários online no topo do chat.
---

**Como ficou no código - Solução duplicação de mensagens:**
- **Servidor (`socket-server.ts`):** envia `{ type: "joined", userId }` no `join` e inclui `userId` no broadcast de `{ type: "chat" }`.
- **Frontend (`useChatSocket.ts`):** salva `userIdRef.current = serverEvent.userId` e compara `mine: serverEvent.userId === userIdRef.current`.
