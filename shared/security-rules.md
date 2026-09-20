# Regras de Segurança EFCsys

- Nunca versionar credenciais, chaves privadas ou service-role keys.
- Aplicar menor privilégio.
- Validar autorização no backend, não apenas na interface.
- Usar RLS/policies adequadas para dados expostos pelo Supabase.
- Não confiar em role, user id ou permissões fornecidas pelo cliente.
- Operações privilegiadas devem permanecer server-side.
- Evitar SECURITY DEFINER sem necessidade e revisão explícita.
- Logs não devem expor segredos ou dados sensíveis.
