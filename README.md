# dudu
# Preparar site ACECO para GitHub / GitHub Pages

Resumo rápido:
- Mova todos os seus arquivos de mídia (vídeos e imagens locais) para uma pasta `assets/` no mesmo nível do `index.html`.
- Renomeie os arquivos para nomes "seguros" (sem espaços, sem acentos, letras minúsculas). Ex.: `Keevx_image_to_video_2025-12-25 08_22_00.mp4` -> `clip-01.mp4`.
- Atualize o `index.html` (já feito neste repositório) para usar caminhos relativos `./assets/arquivo.ext`.
- Se algum arquivo de vídeo for maior que 100 MB, use Git LFS (instruções abaixo) ou hospede o vídeo externamente (YouTube / CDN).

Exemplo de estrutura de pastas (recomendada):
```
/ (raiz do repositório)
  index.html
  /assets
    bg.mp4
    clip-01.mp4
    clip-02.mp4
    image-01.png
    image-02.png
```

Passos para subir para o GitHub e publicar com GitHub Pages:

1. Criar repo (local -> remoto)
```bash
# no diretório do seu site
git init
git add .
git commit -m "Site ACECO - inicial"
git branch -M main
# adicione o origin apontando para o seu repositório no GitHub
git remote add origin https://github.com/<seu-usuario>/<seu-repo>.git
git push -u origin main
```

2. Git LFS (apenas se vídeos > 100 MB)
```bash
# instalar git-lfs (sistema depende do SO)
git lfs install
git lfs track "*.mp4"
git add .gitattributes
git add assets/*.mp4
git commit -m "Track mp4 with LFS"
git push origin main
```
OBS: GitHub limita arquivos normais a 100 MB. Use LFS para arquivos maiores ou hospede em outro lugar.

3. Habilitar GitHub Pages
- Vá em Settings > Pages (no GitHub do repositório) e escolha a branch `main` e a pasta `/ (root)` como fonte. Salve.
- O site estará disponível em `https://<seu-usuario>.github.io/<seu-repo>/` (para Project Pages) ou `https://<seu-usuario>.github.io/` se você usar o repositório `username.github.io`.

4. Observações importantes
- Use caminhos relativos (./assets/arquivo) — assim funciona tanto em Pages quanto localmente.
- Nomes de arquivos são case-sensitive no GitHub (Linux). `image.PNG` ≠ `image.png`.
- Evite espaços e caracteres especiais: substitua por `-` ou `_`.
- Se ainda quiser manter arquivos muito pesados fora do repo, recomendo hospedar os vídeos no YouTube/Cloud Storage e embedar/usar o link no site.

Se quiser, eu posso:
- Gerar uma lista automática de renomeação dos seus arquivos locais (me envie os nomes atuais).
- Criar os comandos Git com `git lfs` adaptados aos seus arquivos.
- Gerar um arquivo .gitignore sugerido.

Quer que eu gere agora os comandos exatos para renomear e empurrar seus arquivos (me envie os nomes atuais ou confirme que usará os nomes sugeridos: `bg.mp4`, `clip-01.mp4`, `clip-02.mp4`, `image-01.png`, `image-02.png`)? 
