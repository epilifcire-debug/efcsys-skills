# Supabase — EFCsys

## Quando usar
Banco, Auth, Storage, RLS, RPC, Edge Functions ou backend Supabase.

## Instruções
- Preservar schema/migrations existentes quando possível.
- Tratar autenticação e autorização separadamente.
- Aplicar RLS coerente com os papéis reais.
- Nunca expor service-role no cliente.
- Evitar SECURITY DEFINER sem necessidade.
- Corrigir a causa do problema sem enfraquecer segurança.
- Não alterar schema/policies não relacionados.
