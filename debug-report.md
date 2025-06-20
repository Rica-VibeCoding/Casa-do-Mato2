# 🔍 Debug Report - Casa do Mato Checklist

## 📊 **Problemas Identificados e Correções**

### ❌ **1. Erro HTTP 409 Conflict**
**Sintoma:** POST retornando 409 Conflict no console
**Causa:** Lógica falha de UPDATE/INSERT tentando inserir registros já existentes
**Solução:** Implementado UPSERT com `Prefer: resolution=merge-duplicates`

### ❌ **2. Headers Duplicados**
**Sintoma:** Headers sendo definidos tanto na função `supabaseRequest` quanto nas chamadas individuais
**Causa:** Duplicação de headers `apikey`, `Authorization` e `Content-Type`
**Solução:** Removido headers duplicados, mantendo apenas o `Prefer` específico de cada requisição

### ❌ **3. Variável Indefinida**
**Sintoma:** `SUPABASE_ANON_KEY` sem prefixo `CONFIG.`
**Causa:** Inconsistência na nomenclatura da variável
**Solução:** Corrigido para `CONFIG.SUPABASE_ANON_KEY`

### ❌ **4. Favicon 404**
**Sintoma:** Erro no console sobre favicon.ico não encontrado
**Causa:** Falta de ícone definido
**Solução:** Adicionado favicon SVG inline

## 🛠️ **Melhorias Implementadas**

### ✅ **1. Sistema UPSERT Robusto**
```javascript
// Nova abordagem com fallback para UPDATE em caso de conflito
const response = await supabaseRequest(CONFIG.TABLE_NAME, {
    method: 'POST',
    body: JSON.stringify(upsertData),
    headers: {
        'Prefer': 'resolution=merge-duplicates,return=minimal'
    }
});

// Fallback para UPDATE se ainda der 409
if (response.status === 409) {
    // Tenta UPDATE direto
}
```

### ✅ **2. Logs Detalhados**
- `[SAVE]` para operações de salvamento
- `[LOAD]` para carregamento de dados
- `[UI]` para interações do usuário
- `[QUEUE]` para processamento da fila

### ✅ **3. Indicador Visual de Salvamento**
- Checkbox pulsa em laranja durante salvamento
- Removido automaticamente após sucesso/erro

### ✅ **4. Botão de Teste Debug**
- Botão "🧪 Test" no canto superior direito
- Testa salvamento isolado para debugging

## 🧪 **Como Testar**

### **1. Teste Básico**
1. Abra o Console (F12)
2. Marque/desmarque qualquer tarefa
3. Observe os logs:
   ```
   [UI] Task docs-imovel-1 alterada para: true
   [SAVE] Iniciando salvamento UPSERT - Task: docs-imovel-1, Status: true
   [SAVE] ✅ UPSERT bem-sucedido para docs-imovel-1
   ```

### **2. Teste do Botão Debug**
1. Clique no botão "🧪 Test" no canto superior direito
2. Deve mostrar alert de sucesso
3. Console deve mostrar logs detalhados

### **3. Verificação no Banco**
```sql
-- Ver registros mais recentes
SELECT task_id, completed, atualizado_em 
FROM casa_do_mato 
ORDER BY atualizado_em DESC 
LIMIT 10;
```

## 📝 **Monitoramento**

### **Logs de Sucesso Esperados:**
```
[LOAD] Iniciando carregamento do Supabase...
[LOAD] ✅ Carregados 65 registros do Supabase
[SAVE] Iniciando salvamento UPSERT - Task: test-debug-123, Status: true
[SAVE] ✅ UPSERT bem-sucedido para test-debug-123
```

### **Logs de Erro a Investigar:**
```
[SAVE] ❌ Erro ao salvar task-id: HTTP Error: 409
[QUEUE] Erro ao processar fila: [detalhes]
[LOAD] ❌ Erro ao carregar do Supabase: [detalhes]
```

## 🚀 **Próximos Passos (Recomendações)**

### **1. Arquitetura de Dados**
- Separar tabelas para checklist e listas customizadas
- Implementar versionamento de dados
- Adicionar índices para performance

### **2. Sincronização Avançada**
- WebSockets do Supabase para tempo real
- Conflict resolution para múltiplos dispositivos
- Retry com exponential backoff

### **3. UX Melhorias**
- Toast notifications para erros
- Modo offline mais robusto
- Indicadores de sincronização por seção

## ⚠️ **Itens para Produção**

1. **Remover botão de teste**: Linha 697-701 em index.html
2. **Remover logs de console**: Manter apenas erros críticos
3. **Implementar rate limiting**: Para evitar spam de requisições
4. **Adicionar monitoramento**: Sentry ou similar para erros em produção
5. **Validação de dados**: Sanitizar inputs antes de salvar 