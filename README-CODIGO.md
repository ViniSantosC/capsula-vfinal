# Código-fonte — 3DM · O que fica

Este pacote contém a interface da cápsula de memórias, os estilos, os scripts de galeria/acessibilidade e um servidor Express com cartas protegidas por senha.

## O que foi preparado

- Cada carta pode ter uma senha própria.
- Senhas são armazenadas somente como hash `scrypt-v1`, nunca em texto puro.
- Mensagens e fotos individuais só são entregues depois da senha correta.
- Fotos individuais ficam fora da pasta pública e recebem URL temporária.
- Cartas sem foto usam uma apresentação de texto em tela cheia, sem coluna vazia.
- As referências do HTML foram alinhadas aos nomes reais de `frontend/img`, incluindo espaços, acentos e extensões JPG/WEBP.
- Ao clicar ou focar na busca, as cartas cadastradas aparecem sem exigir uma primeira pesquisa.
- Há limitação básica de tentativas para reduzir tentativas automáticas.
- O modelo de cadastro está em `backend/homenagens.json.example`.
- O passo a passo completo está em [`GUIA-DEPLOY-E-CARTAS.md`](GUIA-DEPLOY-E-CARTAS.md).

## Conteúdo pessoal não incluído

As mensagens de exemplo ficam em `backend/homenagens.json` para a busca funcionar logo após a instalação. Troque-as antes de publicar e não reutilize a senha provisória. Fotos das cartas ficam em `frontend/img/homenagens` e são bloqueadas para acesso direto; o servidor só as entrega pela rota protegida após a senha.

## Execução local

```bash
cd backend
npm ci
cp homenagens.json.example homenagens.json
# edite homenagens.json e substitua os hashes/mensagens de exemplo
npm start
```

A aplicação abre em `http://localhost:3000`. Para gerar o hash de uma senha individual:

```bash
cd backend
node script.js "senha privada da carta"
```

Copie a saída para o campo `senhaHash` da carta correspondente. Nunca use a senha real dentro de HTML, JavaScript, Git ou mensagens públicas.
