# Instruções de Deploy - Documentação Lazarus

## 📦 Conteúdo do ZIP

O arquivo `lazarus-docs-complete.zip` contém:

```
lazarus-docs/
├── site/                    # Site estático pronto para deploy
│   ├── index.html          # Página inicial
│   ├── architecture/       # Páginas de arquitetura
│   ├── apis/               # Páginas de APIs
│   ├── guides/             # Páginas de guias
│   ├── deployment/         # Páginas de deployment
│   ├── troubleshooting/    # Páginas de troubleshooting
│   ├── assets/             # CSS, JS, imagens
│   └── search/             # Índice de busca
├── docs/                   # Arquivos fonte Markdown
├── mkdocs.yml              # Configuração do MkDocs
└── DEPLOY-INSTRUCTIONS.md  # Este arquivo
```

## 🚀 Opções de Deploy

### 1. Servidor Web Simples (Apache/Nginx)

**Passos:**
1. Extraia o ZIP no seu servidor
2. Copie o conteúdo da pasta `site/` para o diretório web do seu servidor
3. Configure o servidor para servir arquivos estáticos

**Exemplo Nginx:**
```nginx
server {
    listen 80;
    server_name docs.lazarus.com;
    root /var/www/lazarus-docs;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
```

**Exemplo Apache:**
```apache
<VirtualHost *:80>
    ServerName docs.lazarus.com
    DocumentRoot /var/www/lazarus-docs
    DirectoryIndex index.html
</VirtualHost>
```

### 2. GitHub Pages

**Passos:**
1. Crie um repositório no GitHub
2. Faça upload do conteúdo da pasta `site/`
3. Ative GitHub Pages nas configurações do repositório
4. Selecione a branch principal como source

### 3. Netlify

**Passos:**
1. Acesse [netlify.com](https://netlify.com)
2. Arraste a pasta `site/` para a área de deploy
3. Sua documentação estará online em segundos

### 4. Vercel

**Passos:**
1. Instale Vercel CLI: `npm i -g vercel`
2. Na pasta `site/`, execute: `vercel`
3. Siga as instruções para deploy

### 5. AWS S3 + CloudFront

**Passos:**
1. Crie um bucket S3
2. Faça upload do conteúdo da pasta `site/`
3. Configure o bucket para hosting estático
4. (Opcional) Configure CloudFront para CDN

## 🔧 Atualizações Futuras

Para atualizar a documentação:

1. **Edite os arquivos Markdown** na pasta `docs/`
2. **Regenere o site** com: `mkdocs build`
3. **Faça deploy** do novo conteúdo da pasta `site/`

## 📋 Requisitos do Servidor

- **Servidor Web**: Apache, Nginx, ou qualquer servidor de arquivos estáticos
- **HTTPS**: Recomendado para produção
- **Compressão**: Gzip recomendado para melhor performance

## 🌐 URLs Importantes

- **Site Publicado**: [URL será fornecida após deploy]
- **Documentação MkDocs**: https://www.mkdocs.org/
- **Material Theme**: https://squidfunk.github.io/mkdocs-material/

## 📞 Suporte

Para dúvidas sobre a documentação ou deploy, consulte:
- Documentação oficial do MkDocs
- Guias de deploy do seu provedor escolhido
- Documentação do Material Theme

---

**Criado por**: Manus AI  
**Data**: Setembro 2024  
**Versão**: 1.0

