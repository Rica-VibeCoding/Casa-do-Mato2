# 🏡 Casa do Mato - Checklist de Compra

Aplicação web para acompanhar o processo de compra da propriedade "Casa do Mato", onde os pais faleceram deixando 5 herdeiros (Rogério, Rosangela, Vilma, Gego, Daniela), com 4 irmãos concordando em vender os direitos de herança para Daniela.

## ✨ Funcionalidades

- **📋 Checklist Completo**: 8 seções organizadas com todas as etapas do processo
- **☁️ Sincronização em Tempo Real**: Integração com Supabase para backup automático
- **📱 Design Responsivo**: Interface otimizada para mobile e desktop
- **🔄 Backup Local**: Funciona offline com sincronização automática
- **📊 Progresso Visual**: Acompanhamento do percentual de conclusão
- **🎯 Interface Intuitiva**: Design moderno com feedback visual

## 🗂️ Seções do Checklist

1. **📋 Informações do Negócio**
2. **🏠 Documentação do Imóvel**
3. **👨‍👩‍👧‍👦 Documentação dos Pais Falecidos**
4. **👥 Documentação dos 4 Irmãos**
5. **📄 Documentação da Daniela**
6. **📝 Preparação do Contrato**
7. **✍️ Execução do Contrato**
8. **🎯 Pós-Venda**

## 🚀 Tecnologias Utilizadas

- **HTML5** - Estrutura semântica
- **CSS3** - Design responsivo e animações
- **JavaScript** - Lógica da aplicação
- **Supabase** - Backend e banco de dados
- **PWA Ready** - Instalável como app

## 🔧 Configuração

### Supabase
- **Projeto**: nzgifjdewdfibcopolof
- **URL**: https://nzgifjdewdfibcopolof.supabase.co
- **Tabela**: casa_do_mato

### Estrutura da Tabela
```sql
CREATE TABLE casa_do_mato (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  task_id TEXT UNIQUE NOT NULL,
  completed BOOLEAN DEFAULT false,
  completed_at TIMESTAMP WITH TIME ZONE,
  session_id TEXT,
  user_info JSONB,
  criado_em TIMESTAMP WITH TIME ZONE DEFAULT now(),
  atualizado_em TIMESTAMP WITH TIME ZONE DEFAULT now()
);
```

## 📱 Como Usar

1. **Acesse a aplicação** no navegador
2. **Marque as tarefas** conforme forem sendo concluídas
3. **Acompanhe o progresso** na barra superior
4. **Sincronização automática** com a nuvem

## 🌐 Deploy

### Hostinger
- Upload do arquivo `checklist-casa-mato.html` para a pasta `public_html`
- Acesso via: `https://seudominio.com/checklist-casa-mato.html`

### GitHub Pages (Alternativa)
- Ative GitHub Pages nas configurações do repositório
- Acesso via: `https://rica-vibecoding.github.io/Casa-do-Mato/checklist-casa-mato.html`

## 👥 Contexto Familiar

**Situação**: Pais falecidos, 5 herdeiros
- **Rogério** - Irmão (vendendo direitos)
- **Rosangela** - Irmã (vendendo direitos)  
- **Vilma** - Irmã (vendendo direitos)
- **Gego** - Irmão (vendendo direitos)
- **Daniela** - Irmã (comprando os direitos)

## 📞 Suporte

Para dúvidas ou problemas, consulte os logs do navegador (F12 → Console) ou entre em contato.

---

**Desenvolvido com ❤️ para facilitar o processo de compra da Casa do Mato** 

<!-- Teste de deploy automático -->
