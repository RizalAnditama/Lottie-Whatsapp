🧩 Lottie Sticker Builder (WAS) — Beta

Transforma uma imagem (buffer ou arquivo) em uma figurinha animada ".was" (Lottie) pronta pra usar no WhatsApp.

---

⚡ Instalação

1. Clona ou baixa o projeto

git clone https://github.com/Pedrozz13755/Lottie-Whatsapp.git
cd Lottie-Whatsapp

ou só joga o arquivo no teu projeto mesmo.

---

2. Instala dependências

Esse código usa só módulos nativos, mas precisa ter o "zip" instalado no sistema.

No Linux (Termux/Ubuntu):

pkg install zip
# ou
apt install zip

---

📦 Estrutura esperada

Você precisa de uma pasta base do Lottie (exemplo):

src/
 └── exemple/
      └── animation/
           └── animation_secondary.json

Esse JSON precisa ter uma imagem em base64 dentro (o código vai substituir).

---

🚀 Como usar

Importa a função

const { buildLottieSticker } = require("./src/index");

---

Exemplo simples

const output = await buildLottieSticker({
  baseFolder: path.resolve(__dirname, "src", "exemple"),
  buffer: dfileBuffer, // imagem em buffer
  mime: "image/jpeg",
  output: path.resolve(__dirname, "jurubeba.was")
});

---

Enviar no WhatsApp (Baileys)

await client.sendMessage(from, {
  sticker: fs.readFileSync("./jurubeba.was"),
  mimetype: "application/was"
});

---

🧠 Parâmetros

Nome| Tipo| Obrigatório| Descrição
"baseFolder"| string| ✅| Pasta base do Lottie
"buffer"| Buffer| ❌| Imagem em memória
"imagePath"| string| ❌| Caminho da imagem
"mime"| string| ❌| Tipo da imagem (auto detecta se tiver path)
"output"| string| ❌| Caminho do ".was" final
"jsonRelativePath"| string| ❌| Caminho do JSON dentro da base

---

⚠️ Regras importantes

- Precisa enviar buffer OU imagePath
- Formatos suportados:
  - PNG
  - JPG / JPEG
  - WEBP
- O JSON precisa ter uma imagem base64 já existente (ele só substitui)

---

💥 Erros comuns

- "Mime não detectado" → tu não passou mime nem path
- "JSON sem assets" → JSON inválido
- "Nenhuma imagem base64 encontrada" → teu Lottie não tem imagem embutida
- "zip não encontrado" → não instalou zip no sistema

---

🛠️ Dica braba

Se quiser usar direto com imagem do WhatsApp:

const buffer = await getFileBuffer(message, "image");

E já manda no builder.

---

🚧 Status

«⚠️ VERSÃO BETA

Pode quebrar dependendo do Lottie usado.
Ainda não trata todos os tipos de animação.»

---

👑 Créditos

Desenvolvido por Pedrozz Mods

Se isso aqui te ajudou, já sabe né… não custa nada dar aquele crédito 😏

---