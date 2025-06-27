# 📖 Guia de Configuração do GitHub Pages

## Passo a passo detalhado para configurar o deploy automático:

### 1. Configurações do Repositório

#### a) Habilitar GitHub Pages com GitHub Actions:

1. Vá para `Settings` > `Pages`
2. Em **"Source"**, selecione **"GitHub Actions"**
3. **NÃO** selecione "Deploy from a branch"

#### b) Configurar permissões para GitHub Actions:

1. Vá para `Settings` > `Actions` > `General`
2. Em **"Workflow permissions"**, selecione:
   - ✅ **"Read and write permissions"**
3. Marque também:
   - ✅ **"Allow GitHub Actions to create and approve pull requests"**

### 2. Verificar Configurações

#### Certifique-se de que o arquivo `vite.config.ts` tem a configuração correta:

```typescript
export default defineConfig({
  plugins: [react()],
  base: '/mba-devsecops-app/',
  build: {
    outDir: 'dist',
  },
});
```

#### O arquivo de workflow está em:

```
.github/workflows/deploy.yml
```

### 3. Executar o Deploy

#### Faça push das mudanças:

```bash
git add .
git commit -m "feat: configure CI/CD pipeline for GitHub Pages"
git push origin main
```

### 4. Monitorar o Deploy

1. **Acompanhe o pipeline:**

   - Vá para a aba **"Actions"** no GitHub
   - Clique no workflow em execução para ver o progresso

2. **Verificar o resultado:**
   - Após o sucesso, acesse: `https://[seu-usuario].github.io/mba-devsecops-app/`
   - A URL também aparecerá na aba "Pages" das configurações

### 5. Troubleshooting

#### Se o deploy falhar:

1. **Verifique as permissões:**

   - Actions precisam ter permissão de escrita
   - Pages precisa estar configurado para "GitHub Actions"

2. **Verifique o base path:**

   - O `base` no `vite.config.ts` deve coincidir com o nome do repositório

3. **Verifique os logs:**
   - Na aba "Actions", clique no workflow falhado
   - Expanda cada step para ver os erros detalhados

#### URLs importantes:

- **Repositório:** `https://github.com/[usuario]/mba-devsecops-app`
- **Configurações:** `https://github.com/[usuario]/mba-devsecops-app/settings`
- **Actions:** `https://github.com/[usuario]/mba-devsecops-app/actions`
- **Site publicado:** `https://[usuario].github.io/mba-devsecops-app/`

### 6. Atualizações Futuras

Qualquer push para a branch `main` irá automaticamente:

1. Executar o linter
2. Fazer build da aplicação
3. Fazer deploy no GitHub Pages

**Tempo estimado total:** 2-3 minutos por deploy.
