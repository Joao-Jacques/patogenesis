# Patogenesis — site institucional

Site estático de uma página do Patogenesis Laboratório de Diagnóstico Veterinário,
publicado em **https://www.patogenesis.com** pelo GitHub Pages.

Não tem build: HTML, CSS e JS puros. Todo push na `main` vai direto para o ar.

## Estrutura

| Caminho | O que é |
|---|---|
| `index.html` | A página principal (todas as seções) |
| `assets/css/styles.css` | Estilos (cores da marca em `:root`) |
| `assets/js/main.js` | Menu, carrossel, modais e envio do formulário de contato |
| `assets/img/` | Imagens otimizadas usadas no site |
| `assets/img/icons/`, `favicon.ico`, `apple-touch-icon.png`, `site.webmanifest` | Ícones do navegador e da tela inicial |
| `assets/img/og-image.jpg` | Imagem de prévia ao compartilhar o link (1200×630) |
| `politica-de-privacidade.html` | Política de Privacidade (LGPD) |
| `404.html` | Página de erro servida pelo GitHub Pages |
| `robots.txt`, `sitemap.xml` | Orientação para buscadores |
| `llms.txt` | Resumo do laboratório para assistentes de IA |
| `CNAME`, `.nojekyll` | Domínio próprio e publicação sem Jekyll |

`assets/img/originais/` guarda as imagens em alta resolução e **não vai para o repositório**
(está no `.gitignore`), porque tudo que é versionado fica público no site.

## Rodar localmente

```sh
python -m http.server 8000
```

Abra http://localhost:8000. Use um servidor (e não o arquivo direto) para os caminhos
absolutos (`/favicon.ico`, `/assets/...`) funcionarem.

## Ao mudar informações de contato

Telefone, endereço e horário aparecem em vários lugares. Atualize todos:

- `index.html`: seção Contato, rodapé e o bloco JSON-LD no `<head>`
- `llms.txt`
- `politica-de-privacidade.html` (endereço e contato)

O número do WhatsApp nos links `wa.me` fica **sem** o 9º dígito (`556195156979`);
os links `tel:` mantêm o 9.

## Formulário de contato

Enviado pelo [FormSubmit](https://formsubmit.co) para `patogenesislab@gmail.com`
(`CONTACT_ENDPOINT` em `assets/js/main.js`). No primeiro envio, o FormSubmit manda um
e-mail de ativação para esse endereço: até ele ser confirmado, as mensagens não chegam.

## Checklist de publicação

- [ ] DNS: registros A/AAAA do domínio raiz apontando para o GitHub Pages e CNAME de `www` para `<usuario>.github.io`
- [ ] Settings → Pages: domínio `www.patogenesis.com` e **Enforce HTTPS** ligado
- [ ] Settings → Pages: verificar o domínio (evita sequestro do subdomínio)
- [ ] Ativar o FormSubmit (enviar uma mensagem de teste e confirmar o e-mail)
- [ ] Google Search Console: verificar o domínio e enviar `sitemap.xml`
- [ ] Testar a prévia do link no WhatsApp e no [validador de dados estruturados](https://validator.schema.org/)
