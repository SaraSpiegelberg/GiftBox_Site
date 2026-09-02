# Configuração do Domínio giftboxgaming.com.br

## 📋 Checklist de Configuração

### 1️⃣ Preparação do Servidor
O site está pronto para ser hospedado. Você precisa:

- [ ] Contratar hospedagem web (recomendado: Vercel, Netlify ou seu próprio servidor)
- [ ] Ter acesso ao painel de controle do domínio giftboxgaming.com.br
- [ ] Definir a hospedagem preferida

---

## 🚀 Opção A: Vercel (Recomendado - Mais fácil)

### Passo 1: Preparar o repositório
```bash
# Já temos o projeto no GitHub
# Certifique-se que está enviado (git push)
git add .
git commit -m "chore: atualizar identidade visual para Company Logo"
git push origin main
```

### Passo 2: Deploy no Vercel
1. Acesse https://vercel.com
2. Clique em "New Project"
3. Conecte o repositório `GiftBox_Site`
4. Deixe as configurações padrão
5. Clique em "Deploy"

### Passo 3: Apontar o domínio no Vercel
1. No dashboard do Vercel, vá para **Settings > Domains**
2. Adicione o domínio `giftboxgaming.com.br`
3. Siga as instruções para configurar os DNS

### Passo 4: Configurar DNS no seu registrador
1. Acesse o painel do seu registrador (Registro.br, GoDaddy, HostGator, etc)
2. Vá para **Gerenciar DNS** ou **Nameservers**
3. Adicione os registros que o Vercel forneceu:
   - Tipo: **CNAME**
   - Nome: `www`
   - Valor: `cname.vercel-dns.com.`
   
   OU
   
   - Tipo: **A**
   - Valor: `76.76.19.165` (pode variar)

4. Aguarde a propagação (5-48 horas)

---

## 🏠 Opção B: Netlify

### Passo 1: Deploy no Netlify
1. Acesse https://netlify.com
2. Clique em "New site from Git"
3. Conecte o repositório
4. Build command: deixe em branco (site estático)
5. Deploy

### Passo 2: Configurar domínio
1. No dashboard, vá para **Domain settings**
2. Clique em **Add domain**
3. Digite `giftboxgaming.com.br`
4. Siga as instruções DNS do Netlify

---

## 💻 Opção C: Seu próprio servidor (VPS/Hosting compartilhado)

### Se você tem cPanel/Plesk:
1. Crie uma conta de hospedagem
2. Aumente o limite de subdomínios para incluir o domínio
3. Upload dos arquivos via FTP:
   - `index.html`
   - `styles.css`
   - `script.js`
4. Configure os DNS apontando para o servidor

### Se você tem um servidor Linux:
```bash
# Clone o repositório
git clone https://github.com/SaraSpiegelberg/GiftBox_Site.git
cd GiftBox_Site

# Configure com Nginx (recomendado)
sudo apt update && sudo apt install nginx

# Crie a configuração do site
sudo nano /etc/nginx/sites-available/giftboxgaming.com.br
```

Adicione:
```nginx
server {
    listen 80;
    server_name giftboxgaming.com.br www.giftboxgaming.com.br;
    
    root /home/user/GiftBox_Site;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
```

```bash
# Ative o site
sudo ln -s /etc/nginx/sites-available/giftboxgaming.com.br /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx

# Configure SSL (Let's Encrypt - Gratuito!)
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d giftboxgaming.com.br -d www.giftboxgaming.com.br
```

---

## 🔍 Checklist DNS

Depois de configurar, teste com:
```bash
# Verificar se o domínio aponta corretamente
nslookup giftboxgaming.com.br

# Ou
dig giftboxgaming.com.br

# Ou
ping giftboxgaming.com.br
```

---

## 📧 Contato & Email

Para recepcionar emails, configure:
- **MX Record** (Mail Exchange) no seu registrador
- Recomendado: Google Workspace, Mailgun ou seu servidor SMTP

---

## 📱 Próximos Passos Recomendados

- [ ] Adicionar favicon (pequeno ícone na aba do navegador)
- [ ] Implementar formulário de contato funcional
- [ ] Adicionar Analytics (Google Analytics)
- [ ] Configurar SSL/HTTPS (gratuito via Let's Encrypt)
- [ ] Otimizar SEO (meta tags, Open Graph)
- [ ] Adicionar sistema de pedidos/checkout
- [ ] Implementar WhatsApp API para contato

---

## ❓ Dúvidas?

Se tiver problemas na propagação DNS:
- Aguarde 24-48h
- Limpe o cache do DNS: `ipconfig /flushdns` (Windows) ou `sudo dscacheutil -flushcache` (Mac)
- Use https://mxtoolbox.com para verificar registros

Pronto! Seu site está 100% funcional e aguardando o apontamento do domínio. 🚀
