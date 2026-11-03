# Mini Bazar

Um mini-bazar pessoal, para vendas de produtos novos e semi-novos ou usados.

Site 100% estático (GitHub Pages): vitrine para clientes + painel admin que edita o catálogo direto no repositório.

## Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | Vitrine pública: grade, busca, filtro por categoria, página de detalhe e botão de WhatsApp |
| `admin.html` | Painel do vendedor: adicionar/editar/excluir, marcar como vendido, subir fotos |
| `products.json` | O "banco de dados" (o catálogo) |
| `config.js` | Nome do bazar e número do WhatsApp |
| `img/` | Fotos dos produtos (criada automaticamente pelo admin) |

## Publicar

1. Suba todos os arquivos na raiz do repositório.
2. **Settings → Pages → Deploy from a branch → `main` / root**.
3. O site fica em `https://SEU-USUARIO.github.io/NOME-DO-REPO/`.

## Configurar o WhatsApp

No console do navegador (F12), rode `btoa("5586999999999")` com o seu número
(país + DDD + número, só dígitos) e cole o resultado em `whatsappB64` no `config.js`.

## Configurar o admin

1. GitHub → Settings → Developer settings → **Fine-grained personal access tokens** → Generate new token.
2. Repository access: **Only select repositories** → escolha só este repositório.
3. Permissions → Repository → **Contents: Read and write**. Defina validade curta (ex.: 90 dias).
4. Abra `https://SEU-USUARIO.github.io/NOME-DO-REPO/admin.html`, informe usuário, repositório e token.

Cada salvamento vira um commit; o site atualiza em ~1 minuto. Fotos são reduzidas para
1200 px (JPEG) no navegador antes do envio.

## QR code

Gere um QR com a URL do site em qualquer gerador (ex.: qr-code-generator.com ou `qrencode -o qr.png URL`) e imprima para usar em cartazes e no bazar físico.

## Segurança e privacidade

- **O catálogo é público por natureza.** Tudo que a vitrine mostra a um cliente também pode ser lido por qualquer pessoa em `products.json`; criptografar não adianta, porque a chave teria de estar no próprio site. Por isso, não coloque nada sensível no JSON (endereço, CPF, dados pessoais).
- **Admin protegido pelo token, não pela página.** `admin.html` pode ser público: sem um token válido ele não faz nada. O que importa é proteger o token (escopo de um repositório, validade curta, não compartilhar; se vazar, revogue em Settings).
- **WhatsApp codificado em base64** apenas atrapalha robôs simples que varrem o HTML; quem abrir o site e clicar no botão verá o número. Para menos spam, use o WhatsApp Business e bloqueie/denuncie abordagens indesejadas.
- **WhatsApp vs. e-mail:** WhatsApp é mais rápido para fechar venda; e-mail tende a receber mais spam automatizado. Mantenha só WhatsApp, ou use um e-mail dedicado ao bazar.
- Pagamento: combine por Pix diretamente e, para itens de valor, prefira retirada em mãos.
