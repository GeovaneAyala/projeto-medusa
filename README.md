```markdown
# Auditoria de Segurança: Simulação de Ataques de Força Bruta

Este repositório contém a documentação e os artefactos técnicos resultantes do desafio de segurança ofensiva. O projeto foca-se na implementação e documentação de cenários de ataque de força bruta utilizando o **Kali Linux** e a ferramenta **Medusa**, tendo como alvos os ambientes vulneráveis **Metasploitable 2** e **DVWA**.

## Objetivos Alcançados

* Compreensão de ataques de força bruta em múltiplos serviços (FTP, Web, SMB).
* Utilização prática do Kali Linux e do Medusa em ambiente de testes controlado.
* Identificação de vulnerabilidades comuns de autenticação e proposta de soluções de mitigação.
* Estruturação de documentação técnica para portfólio.

## Configuração do Ambiente

O laboratório foi construído de forma isolada para garantir a segurança dos testes:
* **Hypervisor:** VirtualBox
* **Configuração de Rede:** Rede Interna (*host-only*)
* **Máquina Atacante:** Kali Linux
* **Máquinas Alvo:** Metasploitable 2 e DVWA

## Execução dos Testes e Comandos

> **Nota:** Substitua os espaços reservados como `<IP_ALVO>` e `<WORDLIST>` pelos valores e ficheiros correspondentes utilizados durante o seu teste.

### 1. Ataque de Força Bruta em FTP
* **Alvo:** Serviço FTP do Metasploitable 2.
* **Descrição:** Tentativa de descobrir as credenciais de acesso através de dicionários de palavras-passe.
* **Comando de Exemplo:**
  ```bash
  medusa -h <IP_ALVO> -u <NOME_UTILIZADOR> -P <FICHEIRO_WORDLIST> -M ftp

```

* **Validação de Acesso:** [Descreva aqui se o acesso foi obtido e com que utilizador]

### 2. Automação de Tentativas em Formulário Web (DVWA)

* **Alvo:** DVWA (Damn Vulnerable Web Application).
* **Descrição:** Exploração do formulário de login web utilizando força bruta.
* **Comando/Ferramenta:** [Inserir o comando exato utilizado com o módulo web do Medusa ou outra ferramenta adaptada]
* **Validação de Acesso:** [Descreva os resultados obtidos no painel do DVWA]

### 3. Enumeração e Password Spraying em SMB

* **Alvo:** Serviço SMB do Metasploitable 2.
* **Descrição:** Enumeração prévia de utilizadores válidos seguida de um ataque de *password spraying* (testar uma palavra-passe comum em várias contas).
* **Comando de Enumeração (Exemplo):**
```bash
enum4linux -U <IP_ALVO>

```


* **Comando de Password Spraying (Medusa):**
```bash
medusa -h <IP_ALVO> -U <FICHEIRO_UTILIZADORES_ENUMERADOS> -p "<PALAVRA_PASSE_COMUM>" -M smbnt

```


* **Validação de Acesso:** [Descreva os utilizadores comprometidos com sucesso]

## Recomendações de Mitigação

Com base nos testes realizados, recomendam-se as seguintes políticas de segurança para proteger os serviços auditados:

* **Implementação de Bloqueio de Conta (Account Lockout):** Bloquear a conta temporariamente após um número predefinido de tentativas de login falhadas (ex: 5 tentativas).
* **Políticas de Palavras-passe Robustas:** Exigir complexidade (letras, números, símbolos) e um comprimento mínimo.
* **Autenticação Multifator (MFA):** Adicionar uma camada secundária de verificação para acessos a serviços críticos, como plataformas Web e VPNs.
* **Desativação de Serviços Obsoletos:** Substituir serviços de texto simples como o FTP tradicional por alternativas seguras como SFTP ou FTPS.
* **Monitorização e Resposta:** Configurar um SIEM/IDS para alertar a equipa de segurança sobre padrões de tráfego anómalos ou picos de falhas de autenticação.

## Estrutura do Repositório e Evidências

* `README.md`: Documentação principal do projeto.
* `/images`: Diretório contendo as capturas de ecrã (screenshots) que evidenciam a execução dos comandos e a validação dos acessos.
* `wordlist_custom.txt`: [Exemplo] Dicionário de palavras-passe utilizado nos testes.
* `users_smb.txt`: [Exemplo] Ficheiro gerado com a enumeração de utilizadores do serviço SMB.

```

```
# projeto-medusa
