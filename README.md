# Laboratórios de Informática do IMPA Tech

Guia rápido para alunos sobre como usar os laboratórios de informática do IMPA Tech: acesso, armazenamento de arquivos, software disponível, impressão e boas práticas.

> Os trechos marcados com **[PREENCHER]** ainda precisam ser completados com as informações oficiais.

## Sumário

- [Laboratórios disponíveis](#laboratórios-disponíveis)
- [Primeiro acesso](#primeiro-acesso)
- [Login e logout](#login-e-logout)
- [Onde salvar seus arquivos](#onde-salvar-seus-arquivos)
- [Software disponível](#software-disponível)
- [Impressão](#impressão)
- [Acesso remoto](#acesso-remoto)
- [Regras de uso](#regras-de-uso)
- [Dicas](#dicas)
- [Problemas comuns](#problemas-comuns)
- [Suporte](#suporte)

## Laboratórios disponíveis

| Laboratório | Local | Nº de máquinas | Sistema operacional | Horário |
|---|---|---|---|---|
| [PREENCHER] | [PREENCHER] | [PREENCHER] | [PREENCHER] | [PREENCHER] |

Os laboratórios podem estar reservados para aulas. Confira a agenda de ocupação em: **[PREENCHER: link ou local da agenda]**.

## Primeiro acesso

1. Obtenha suas credenciais: **[PREENCHER: como o aluno recebe usuário/senha — ex.: mesmo login do e-mail institucional, cadastro na TI]**.
2. Faça login em qualquer máquina do laboratório.
3. Troque a senha inicial, se solicitado: **[PREENCHER: procedimento/link]**.
4. Verifique se sua pasta pessoal está acessível (veja [Onde salvar seus arquivos](#onde-salvar-seus-arquivos)).

## Login e logout

- Use seu usuário **[PREENCHER: formato, ex.: `nome.sobrenome`]** e sua senha institucional.
- **Sempre faça logout** ao terminar. Apenas bloquear a tela deixa sua sessão aberta e impede outras pessoas de usar a máquina.
- Não desligue as máquinas, a menos que seja instruído a fazê-lo. **[PREENCHER: confirmar política]**
- Nunca compartilhe sua senha. Você é responsável por tudo que for feito com sua conta.

## Onde salvar seus arquivos

| Local | Caminho | Persistente? | Observações |
|---|---|---|---|
| Pasta pessoal (rede) | **[PREENCHER]** | Sim | Acessível de qualquer máquina do laboratório. Cota: **[PREENCHER]** |
| Disco local / área temporária | **[PREENCHER, ex.: `/tmp`]** | **Não** | Pode ser apagado ao reiniciar ou fazer logout |

Dicas:

- Arquivos salvos **fora** da pasta pessoal podem ser apagados sem aviso.
- Faça backup dos trabalhos importantes (Git, nuvem institucional, pendrive).
- Para saber quanto espaço está usando: **[PREENCHER: comando, ex.: `quota -s` ou `du -sh ~`]**.

## Software disponível

**[PREENCHER: lista oficial]**. Exemplos de categorias:

- **Programação:** Python, Jupyter, compiladores C/C++, Julia, R, ...
- **Editores e IDEs:** VS Code, ...
- **Matemática e computação científica:** ...
- **Documentos:** LaTeX, LibreOffice, ...

### Instalando pacotes sem permissão de administrador

As máquinas vêm com o **conda**. Ao fazer login, você já entra automaticamente no ambiente **`ambiente_aluno`**, que usa o **Python 3.13** (versão padrão do laboratório) e tem um conjunto padronizado de bibliotecas, igual em todas as máquinas.

Você **não tem permissão para instalar pacotes no `ambiente_aluno`**. Para usar um pacote que não está lá, saia desse ambiente e crie um ambiente seu:

```bash
# Ver quais pacotes já existem no ambiente padrão
conda list

# Sair do ambiente_aluno
conda deactivate

# Criar um ambiente próprio com o Python 3.13, o mesmo do laboratório
# (troque a versão só se o seu projeto exigir outra)
conda create -n meu-projeto python=3.13 numpy matplotlib

# Ativar o novo ambiente e instalar o que precisar
conda activate meu-projeto
conda install nome-do-pacote    # ou: pip install nome-do-pacote
```

Comandos úteis:

```bash
conda env list                   # lista seus ambientes (o ativo aparece com *)
conda activate ambiente_aluno    # volta para o ambiente padrão
conda env remove -n meu-projeto  # apaga um ambiente que não usa mais
```

### Instalando tudo de uma vez com `requirements.txt`

Em vez de instalar pacote por pacote, liste todos em um arquivo `requirements.txt` na pasta do seu projeto, um por linha:

```text
numpy
pandas>=2.0
matplotlib
scikit-learn==1.5.2
```

- `pacote` instala a versão mais recente disponível.
- `pacote>=2.0` exige uma versão mínima.
- `pacote==1.5.2` fixa uma versão exata (bom para garantir que o código rode igual em qualquer máquina).

Depois, com o seu ambiente ativado, instale tudo com um único comando:

```bash
conda activate meu-projeto
pip install -r requirements.txt
```

Se você já instalou os pacotes manualmente e quer gerar o arquivo a partir do ambiente atual:

```bash
pip freeze > requirements.txt
```

Guarde o `requirements.txt` junto com o código (por exemplo, no Git). Assim você recria o ambiente em outra máquina, ou depois de apagá-lo, em poucos comandos:

```bash
conda create -n meu-projeto python=3.13
conda activate meu-projeto
pip install -r requirements.txt
```

Dicas:

- O novo ambiente começa **vazio**, sem as bibliotecas do `ambiente_aluno`. Instale nele tudo o que o seu projeto usa.
- A cada novo login você volta para o `ambiente_aluno`. Rode `conda activate meu-projeto` sempre que for usar o seu ambiente.
- Para usar o ambiente no Jupyter ou no VS Code, selecione-o como kernel/interpretador. No Jupyter, pode ser preciso instalar o `ipykernel` no ambiente antes.
- Ambientes conda ocupam bastante espaço da sua cota. Remova os que não usa mais.

Precisa de algum software que não está instalado para uma disciplina? Peça com antecedência em **[PREENCHER: canal]**.

## Impressão

- Impressoras disponíveis: **[PREENCHER]**
- Como imprimir: **[PREENCHER]**
- Cota/limite de impressão: **[PREENCHER]**

## Acesso remoto

**[PREENCHER: se houver acesso via SSH/VPN, descrever aqui. Caso contrário, remover esta seção.]**

```bash
ssh seu.usuario@[PREENCHER-servidor]
```

## Regras de uso

- Não é permitido comer ou beber perto dos computadores.
- Não desconecte cabos, monitores ou periféricos.
- Mantenha silêncio, principalmente durante aulas e provas.
- Não instale software no sistema nem tente alterar configurações das máquinas.
- Durante aulas agendadas, os alunos da turma têm prioridade.
- Respeite as políticas de uso da rede e dos recursos institucionais: **[PREENCHER: link]**.

## Dicas

- **Use Git** para versionar seus trabalhos. Você pode trabalhar de qualquer máquina (ou de casa) e não perde nada se algo for apagado.
- **Salve com frequência** e, de preferência, na pasta pessoal.
- **Não deixe processos pesados rodando** depois de sair; outras pessoas vão usar a máquina.
- **Feche navegadores e sessões** (e-mail, Google, GitHub) antes de fazer logout. Na dúvida, use uma janela anônima.
- **Cuidado com arquivos grandes** (datasets, vídeos, modelos): eles enchem a cota rapidamente. Prefira guardá-los em `/tmp` durante o uso e manter só o essencial na pasta pessoal.
- **Encontrou algo com defeito?** Avise o suporte em vez de tentar consertar.

## Problemas comuns

| Problema | O que tentar |
|---|---|
| Não consigo fazer login | Confira usuário/senha e Caps Lock. Se persistir, contate o suporte. |
| Login trava ou volta para a tela inicial | Provavelmente a cota está cheia. **[PREENCHER: como liberar espaço / contatar suporte]** |
| Meus arquivos sumiram | Verifique se foram salvos na pasta pessoal e não em área temporária. |
| Programa não abre ou não está instalado | Veja [Software disponível](#software-disponível) ou peça ao suporte. |
| Máquina travada | Aguarde alguns minutos. Se não voltar, avise o suporte antes de reiniciar. |

## Suporte

- **E-mail:** [PREENCHER]
- **Local / horário de atendimento:** [PREENCHER]
- **Abertura de chamado:** [PREENCHER]

Ao relatar um problema, informe: laboratório, número/nome da máquina, seu usuário, o que estava fazendo e a mensagem de erro (uma foto da tela ajuda).
