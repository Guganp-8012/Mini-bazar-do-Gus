# Mini Bazar

Um mini-bazar pessoal, para vendas de produtos novos e semi-novos ou usados.

**Acesse o bazar: https://guganp-8012.github.io/Mini-bazar-do-Gus/**

É um site simples e estático, hospedado no GitHub Pages: um catálogo para os clientes e um painel só meu para cadastrar os produtos. Não tem carrinho nem pagamento. A compra é combinada direto comigo pelo WhatsApp.

## O que o site faz

- **Catálogo** com busca e filtro por categoria.
- **Página do produto** com várias fotos, preço, condição e descrição.
- **Status do item:** disponível, reservado ou vendido (itens ocultos não aparecem).
- **Botão de WhatsApp** com a mensagem já preenchida com o nome e o preço do produto.
- **Painel admin** para adicionar, editar e excluir produtos, trocar o status e enviar fotos (até 8 por produto), sem mexer em código.

## Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | Vitrine pública para os clientes |
| `admin.html` | Painel do vendedor (precisa de token, veja abaixo) |
| `products.json` | O catálogo, que funciona como banco de dados |
| `config.js` | Nome do bazar e número do WhatsApp |
| `img/` | Fotos dos produtos (criada automaticamente pelo painel) |

## Publicar

1. Suba todos os arquivos na raiz do repositório.
2. Em **Settings → Pages**, escolha **Deploy from a branch**, branch `master`, pasta `/ (root)`.
3. O site fica em `https://SEU-USUARIO.github.io/NOME-DO-REPO/`.
4. Opcional: na página do repositório, clique na engrenagem de **About** e cole o link do site no campo **Website**. Assim ele aparece em destaque ao lado da descrição.

## Configurar o WhatsApp

No console do navegador (F12), rode `btoa("5586999999999")` com o seu número (país + DDD + número, só dígitos) e cole o resultado em `whatsappB64` no `config.js`.

## Configurar o painel admin

O painel fica em `.../admin.html`. Para conectar:

1. No GitHub, vá em Settings → Developer settings → **Fine-grained personal access tokens** → Generate new token.
2. Em Repository access, escolha **Only select repositories** e marque só este repositório.
3. Em Permissions → Repository, defina **Contents: Read and write**. Escolha uma validade curta (ex.: 90 dias).
4. No painel, informe usuário, repositório, branch (`master`) e o token.

A conexão fica salva no navegador, então é feita uma vez por aparelho. Cada alteração vira um commit e o site atualiza em cerca de 1 minuto. As fotos são reduzidas para 1200 px (JPEG) no navegador antes do envio.

## QR code

Gere um QR com o link do site em qualquer gerador (ex.: qr-code-generator.com ou `qrencode -o qr.png URL`) e imprima para cartazes ou para o bazar físico.

## Segurança e privacidade

- **O catálogo é público por natureza.** Tudo que a vitrine mostra também pode ser lido em `products.json`. Criptografar não adianta, porque a chave teria de ficar no próprio site. Por isso, não coloque nada sensível nele (endereço, CPF, dados pessoais).
- **O painel é protegido pelo token, não pela página.** O `admin.html` pode ser público: sem um token válido ele não faz nada. Proteja o token (escopo de um repositório, validade curta, nunca compartilhe) e, se vazar, revogue em Settings.
- **O WhatsApp está codificado em base64**, o que só atrapalha robôs simples de spam. Quem clicar no botão verá o número. O WhatsApp Business ajuda a filtrar contatos indesejados.
- **Pagamento:** combinado direto por Pix. Para itens de valor, prefira retirada em mãos.
