# WPC Mods for Claude

[English](README.md) · **Português (Brasil)**

Um marketplace do Claude Code que reúne os meus mods num lugar só. Adicionar o marketplace não instala nada: você escolhe quais mods quer, um por um.

## Mods

| Mod | Identificador | O que faz |
| --- | --- | --- |
| [Status Pills](https://github.com/carreirodev/mod-status-pills) | `status-pills` | Faixa de pílulas junto ao prompt: modelo e esforço, contexto, limites de 5 horas e 7 dias com as renovações, projeto e branch |
| [Agents Panel](https://github.com/carreirodev/mod-painel-agents) | `agents-panel` | Painel lateral com todos os agentes da sessão (modelo, esforço, cronômetro e uso de tokens) e os shells em segundo plano |
| [Prompt Enhancer](https://github.com/carreirodev/mod-prompt-enhancer) | `prompt-enhancer` | Botões Enhance e Send acima do prompt: reescreve o rascunho no lugar, mais claro para a IA, sem acrescentar nada |
| [Plan Progress](https://github.com/carreirodev/mod-plan-pill-progress) | `plan-progress` | Barras de progresso do plano, ao vivo, acima do prompt, com sons suaves |

Cada mod mora no seu próprio repositório, com o README dele explicando o uso em detalhe.

## Instalar

1. Numa sessão do Claude Code, adicione o marketplace:

   ```
   /plugin marketplace add carreirodev/wpc-mods-claude
   ```

2. Instale cada mod que quiser pelo identificador, por exemplo:

   ```
   /plugin install status-pills@wpc-mods-claude
   ```

   Ou abra `/plugin`, vá na aba **Discover** e escolha por lá.

3. Abra uma sessão nova, ou rode `/reload-plugins` na sessão aberta.

O WSL tem a sua própria instalação do Claude Code, separada da do Windows: repita os passos dentro do WSL também.

### Se você já instalou um mod pelo repositório dele

Cada mod também tem um marketplace próprio, no repositório dele. Desinstale a cópia antiga antes de instalar por aqui: com o mesmo mod instalado por dois marketplaces, os dois aparecem como ativos, mas só um roda.

Para ver de onde veio cada mod, rode no terminal, fora do Claude Code:

```
claude plugin list
```

O nome depois do `@` é o marketplace. Para remover uma cópia antiga, por exemplo `status-pills@status-pills`:

```
claude plugin uninstall status-pills@status-pills
```

## Atualizar

A atualização não é automática. Para buscar a versão nova de um mod, rode no terminal, fora do Claude Code:

```
claude plugin update status-pills@wpc-mods-claude
```

Depois abra uma sessão nova, ou rode `/reload-plugins`.

Para não ter de lembrar: em `/plugin`, na aba **Marketplaces**, escolha `wpc-mods-claude` e depois **Enable auto-update**.

## Adicionar um mod a este marketplace

Acrescente uma entrada em `plugins`, no arquivo [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json):

- Mod na raiz do repositório dele: `"source": { "source": "github", "repo": "carreirodev/<repo>" }`
- Mod numa subpasta: `"source": { "source": "git-subdir", "url": "carreirodev/<repo>", "path": "<subpasta>" }`

O `name` da entrada precisa ser igual ao `name` do `plugin.json` do mod. Confira com `claude plugin validate .` e envie para o GitHub; quem já tem o marketplace vê o mod novo depois de `/plugin marketplace update wpc-mods-claude`.

Quem instalou só recebe código novo de um mod quando o `version` do `plugin.json` dele muda, então suba a versão a cada release.
