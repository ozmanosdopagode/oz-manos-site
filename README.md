from zipfile import ZipFile
import os

# Criar estrutura dos arquivos
site_folder = "/mnt/data/oz_manos_site"
os.makedirs(site_folder, exist_ok=True)

html_content = """
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Oz Manos do Pagode - Pedidos</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #121212;
      color: #fff;
    }
    header {
      background-color: #000;
      padding: 20px;
      text-align: center;
    }
    header img {
      max-height: 80px;
    }
    .container {
      padding: 20px;
      max-width: 700px;
      margin: 0 auto;
      background-color: #1e1e1e;
      border-radius: 12px;
    }
    h1, h2 {
      color: #f5c518;
    }
    p {
      line-height: 1.6;
    }
    .pix-box {
      background: #2b2b2b;
      padding: 10px;
      border: 2px dashed #f5c518;
      margin: 20px 0;
      text-align: center;
      font-weight: bold;
    }
    .button {
      background-color: #f5c518;
      color: #000;
      padding: 15px;
      text-align: center;
      border: none;
      border-radius: 8px;
      font-size: 18px;
      cursor: pointer;
      width: 100%;
      margin: 20px 0;
    }
    .social {
      text-align: center;
      margin-top: 30px;
    }
    .social a {
      color: #f5c518;
      margin: 0 10px;
      text-decoration: none;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <header>
    <img src="logo.png" alt="Oz Manos do Pagode Logo">
  </header>

  <div class="container">
    <h1>Peça sua Música!</h1>
    <p>Curta o show ao vivo e interaja com a gente fazendo seu pedido musical diretamente por aqui.</p>
    <p>Preencha o formulário abaixo e contribua com o valor que quiser via Pix.</p>

    <div class="pix-box">
      Chave Pix: <br> ozmanosdopagodeluiz@gmail.com
    </div>

    <button class="button" onclick="window.location.href='https://forms.gle/seu-formulario-aqui'">FAZER UM PEDIDO</button>

    <h2>Como funciona?</h2>
    <p>
      1. Clique no botão acima para acessar o formulário de pedidos. <br>
      2. Escolha sua música do repertório. <br>
      3. Faça sua contribuição via Pix (valor livre). <br>
      4. Seu pedido será visto em tempo real e pode ser o próximo!
    </p>

    <div class="social">
      <p>Siga a gente nas redes:</p>
      <a href="#">@ozmanosdopagode</a>
      <a href="#">@luizsambaplay</a>
    </div>
  </div>
</body>
</html>
"""

# Salvar HTML
html_path = os.path.join(site_folder, "index.html")
with open(html_path, "w", encoding="utf-8") as f:
    f.write(html_content)

# Copiar logo
logo_source = "/mnt/data/file-CAkNSBaaUfGDykPWsjmdke"
logo_dest = os.path.join(site_folder, "logo.png")
os.rename(logo_source, logo_dest)

# Criar arquivo ZIP
zip_path = "/mnt/data/oz_manos_site.zip"
with ZipFile(zip_path, "w") as zipf:
    zipf.write(html_path, arcname="index.html")
    zipf.write(logo_dest, arcname="logo.png")

zip_path
