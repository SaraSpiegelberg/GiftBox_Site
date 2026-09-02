# GitHub Pages + GoDaddy - Guia Completo

## ✅ Passo 1: Preparar o repositório (FEITO)

Já criei o arquivo `CNAME` com seu domínio. Agora é só fazer push:

```bash
git add CNAME
git commit -m "docs: adicionar CNAME para giftboxgaming.com.br"
git push origin main
```

---

## 🔧 Passo 2: Ativar GitHub Pages no repositório

1. Acesse: **https://github.com/SaraSpiegelberg/GiftBox_Site**
2. Vá para **Settings** (engrenagem no topo)
3. No menu lateral, clique em **Pages**
4. Em **Build and deployment**:
   - Source: **Deploy from a branch**
   - Branch: **main**
   - Pasta: **/ (root)**
5. Clique em **Save**

GitHub vai gerar uma URL temporária como `https://saraspigelberg.github.io/GiftBox_Site/`

---

## 🌐 Passo 3: Configurar DNS na GoDaddy

### Via DNS Records (Recomendado - mais rápido)

1. Acesse a GoDaddy: **https://godaddy.com**
2. Vá para **Meus Produtos > Domínios**
3. Clique no domínio `giftboxgaming.com.br`
4. Clique em **Gerenciar DNS** ou **DNS**

Procure por registros existentes e **ADICIONE** os seguintes:

#### Opção A: Usando registros A (mais comum)
```
Tipo: A
Nome: @ (ou deixe em branco)
Valor: 185.199.108.153

Tipo: A
Nome: @ (ou deixe em branco)
Valor: 185.199.109.153

Tipo: A
Nome: @ (ou deixe em branco)
Valor: 185.199.110.153

Tipo: A
Nome: @ (ou deixe em branco)
Valor: 185.199.111.153
```

#### Opção B: Usando registros CNAME (alternativa)
```
Tipo: CNAME
Nome: www
Valor: SaraSpiegelberg.github.io
```

---

## 🚀 Passo 4: Ativar HTTPS (automático)

1. Volte ao GitHub Settings > Pages
2. Marque a opção **Enforce HTTPS** 
3. Aguarde ~5 minutos para o certificado ser gerado

---

## ⏱️ Propagação DNS

A propagação pode levar **5 minutos a 48 horas**. Nesse período:
- O site pode estar intermitente
- Use ferramentas para verificar:

```bash
# Verificar DNS (aguarde a propagação)
nslookup giftboxgaming.com.br
dig giftboxgaming.com.br

# Ou acesse: https://mxtoolbox.com
# e digite seu domínio
```

---

## ✨ Resultado Final

Depois que a DNS propagar:
- ✅ `giftboxgaming.com.br` apontará para seu site no GitHub Pages
- ✅ `www.giftboxgaming.com.br` também funcionará
- ✅ HTTPS automático (URL segura com cadeado 🔒)
- ✅ Sem custo adicional de hospedagem

---

## 🔍 Checklist Final

- [ ] Fiz push do arquivo CNAME para GitHub
- [ ] Ativei GitHub Pages no repositório
- [ ] Adicionei os registros DNS na GoDaddy
- [ ] Aguardei 5-48h para propagação
- [ ] Testei acessando `giftboxgaming.com.br`

---

## ❓ Troubleshooting

### Site mostra erro 404
- Verifique se o arquivo CNAME está no repositório
- Certifique-se que o branch é `main` e a pasta é `/ (root)`

### Domínio não funciona após 48h
- Limpe o cache DNS:
  - Windows: `ipconfig /flushdns`
  - Mac: `sudo dscacheutil -flushcache`
  - Linux: `sudo systemctl restart systemd-resolved`

### HTTPS não aparece após 1h
- Espere até 15 minutos para o certificado ser emitido
- Desmarque e marque novamente "Enforce HTTPS" nas Settings

### Remover o domínio customizado (voltarà ao .github.io)
- Exclua o arquivo CNAME do repositório
- Desative GitHub Pages nas Settings

---

## 📞 Suporte

Se precisar ajuda:
- GitHub Docs: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-pages-site
- GoDaddy Support: https://www.godaddy.com/help

Seu site estará 100% funcional em breve! 🎉
