# 🛠️ Guia de Debug - Checklist Casa do Mato

## 📋 Como Debugar o Projeto

### 1. **Atualize a página e abra o Console**
- Abra o `checklist-casa-mato.html` no navegador
- Pressione `F12` ou `Ctrl+Shift+I` para abrir o DevTools
- Vá para a aba `Console`

### 2. **Execute os Diagnósticos**
- Clique no menu (⋮) no canto inferior direito
- Selecione "Executar Diagnósticos"
- Observe os logs no console

### 3. **Teste o Google Apps Script**
- No menu, selecione "Testar Apps Script"
- Veja se há respostas ou erros no console

## 🔧 Configuração do Google Apps Script

### **Passo 1: Acessar o Google Apps Script**
1. Acesse: https://script.google.com/
2. Procure pelo projeto com o ID: `AKfycbzqqo54hBkkVfBzH0q-qbzuOFx2gxWHATqwxgFFDqydXMPXTc8Ujz3RTabLgsy_woYY`

### **Passo 2: Verificar/Criar o Código**
Se o projeto não existe ou está vazio:

1. Crie um novo projeto no Google Apps Script
2. Cole o código do arquivo `google-apps-script-exemplo.gs`
3. Vincule à planilha: https://docs.google.com/spreadsheets/d/1nvsz_blZTP7ia8a2Er6ru1uaZYptplKlBTkwPJoDHns/edit

### **Passo 3: Configurar Permissões**
1. No Apps Script, vá em **Implantar** > **Nova implantação**
2. Tipo: **Aplicativo da Web**
3. Executar como: **Eu (seu email)**
4. Quem tem acesso: **Qualquer pessoa**
5. Clique em **Implantar**
6. **IMPORTANTE**: Copie a nova URL gerada e substitua no HTML

### **Passo 4: Verificar a Planilha**
A planilha deve ter:
- **Coluna A**: task_id
- **Coluna B**: completed  
- **Coluna C**: timestamp

## 🚨 Principais Problemas e Soluções

### **Erro: "Failed to fetch"**
**Causas possíveis:**
- Apps Script não implantado corretamente
- URL incorreta ou expirada
- Problemas de CORS
- Permissões inadequadas

**Solução:**
1. Verifique se o Apps Script está implantado como "Aplicativo da Web"
2. Confirme se as permissões estão como "Qualquer pessoa"
3. Teste a URL diretamente no navegador

### **Erro: "TypeError" ou JSON inválido**
**Causas possíveis:**
- Apps Script retornando HTML de erro em vez de JSON
- Código do Apps Script com problema

**Solução:**
1. Verifique os logs do Apps Script
2. Teste as funções manualmente no editor
3. Confirme se o código está correto

### **Dados não salvam**
**Causas possíveis:**
- Planilha com estrutura incorreta
- Permissões de escrita insuficientes

**Solução:**
1. Verifique se a planilha tem as colunas corretas
2. Confirme permissões de edição
3. Teste salvamento manual no Apps Script

## 📊 Como Verificar se Está Funcionando

### **Teste Manual**
1. Abra o console do navegador
2. Execute: `runDiagnostics()`
3. Analise os resultados de cada teste

### **Teste do Apps Script**
1. Execute: `testAppsScript()`
2. Veja se recebe resposta JSON válida

### **Teste de Salvamento**
1. Marque/desmarque algumas tarefas
2. Verifique se aparecem na planilha
3. Recarregue a página e veja se mantém o estado

## 🔍 Logs de Debug

Agora o sistema tem logs detalhados que mostram:
- ✅ **Verde**: Operações bem-sucedidas
- ❌ **Vermelho**: Erros críticos
- ⚠️ **Amarelo**: Avisos importantes
- 🔬 **Roxo**: Informações de debug

## 📞 Próximos Passos

1. **Execute os diagnósticos** no menu da aplicação
2. **Compartilhe os logs** do console comigo
3. **Verifique se o Apps Script existe** e está configurado
4. **Confirme as permissões** da planilha e do script

---

**💡 Dica**: Mantenha o console aberto enquanto usa a aplicação para acompanhar os logs em tempo real. 