# Automação de Criação e Remoção de Usuários, Pastas, Grupos e Permissões 

Este conjunto de scripts automatiza a criação e remoção de usuários, grupos, pastas e configurações de permissões em um sistema Linux. Ele e útil para ambientes corporativos onde é necessário gerenciar usuários de forma eficiente.

## 📌 Funcionalidades
Os scripts realizam as seguintes operações:

### `IaC_create_settings.sh`
- Cria os diretórios `/publico`, `/adm`, `/ven` e `/sec`.
- Cria os grupos `GRP_ADM`, `GRP_VEN` e `GRP_SEC`.
- Define as permissões corretas para cada diretório.
- Cria usuários e os adiciona aos respectivos grupos.
- Define senhas padrão e obriga os usuarios a alterarem no primeiro login.

### `IaC_delete_settings.sh`
- Remove todos os usuários comuns (com UID maior ou igual a 1001), excluindo suas pastas pessoais.
- Remove todos os grupos criados dinamicamente (com GID maior ou igual a 1001).
  
Obs: Esse arquivo não foi exigido pelo curso, mas resolvi faze-lo ao perceber que podia automatizar as primeiras exclusões que vi o professor fazendo nos primeiros minutos do vídeo de solução do desafio.

## 📂 Estrutura dos Diretórios e Permissões

| Diretório  | Grupo Associado | Permissões |
|------------|----------------|------------|
| /publico  | Todos os usuários | 777 (acesso total) |
| /adm      | GRP_ADM         | 770 (apenas administradores) |
| /ven      | GRP_VEN         | 770 (apenas equipe de vendas) |
| /sec      | GRP_SEC         | 770 (apenas equipe de segurança) |

## 🚀 Como Executar os Scripts

### Criar usuários e grupos
1. Salve o script como `IaC_create_settings.sh`.
2. Dê permissão de execução ao script:
   ```bash
   chmod +x IaC_create_settings.sh
   ```
3. Execute o script como superusuário:
   ```bash
   sudo ./IaC_create_settings.sh
   ```

### Remover usuários e grupos
1. Salve o script como `IaC_delete_settings.sh`.
2. Dê permissão de execução ao script:
   ```bash
   chmod +x IaC_delete_settings.sh
   ```
3. Execute o script como superusuário:
   ```bash
   sudo ./IaC_delete_settings.sh
   ```

## 👥 Usuários Criados

### Grupo: GRP_ADM
- carlos
- maria
- joao

### Grupo: GRP_VEN
- debora
- sebastiana
- roberto

### Grupo: GRP_SEC
- josefina
- amanda
- rogerio

## 🔒 Segurança
- Cada usuário tem a senha inicial `Senha123`, que deve ser alterada no primeiro login.
- O uso de `chpasswd` permite definir a senha de forma segura.
- O script aplica corretamente permissões para evitar acesso indevido entre grupos.

## 🛠 Tecnologias Utilizadas
- Bash Script
- Comandos Linux (`mkdir`, `groupadd`, `useradd`, `chmod`, `chown`, `passwd`, `chage`, `awk`, `userdel`, `groupdel`)

## 📜 Licença
Este conjunto de scripts é fornecido como está, sem garantias. Sinta-se livre para modificar e adaptar conforme necessário.

---
Criado para facilitar a administração de usuários em ambientes Linux! 🚀

