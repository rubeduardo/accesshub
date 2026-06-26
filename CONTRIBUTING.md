# 🤝 Contribuindo para AccessHub

Primeiro, **obrigado por considerar contribuir para o AccessHub**! 🎉

Este projeto existe graças a pessoas como você que dedicam tempo e energia. Quer você seja desenvolvedor, designer, especialista em acessibilidade ou apenas alguém apaixonado por inclusão, sua contribuição é valiosa.

---

## 💡 Por Que Contribuir?

- **Impacto social** - Seu código ajuda pessoas com deficiência
- **Aprendizado** - Pratique skills reais em um projeto significativo
- **Comunidade** - Conheça pessoas incríveis que compartilham seus valores
- **Portfolio** - Mostre suas contribuições open source
- **Inclusão** - Este é um espaço seguro e acolhedor para todos

---

## 🎯 Tipos de Contribuição

### 💻 Desenvolvimento
- **Backend**: FastAPI, Node.js, banco de dados
- **Frontend**: Next.js, React, TypeScript
- **DevOps**: Docker, CI/CD, Infrastructure
- **Testes**: Unit tests, integration tests, E2E tests

**Exemplos de tasks**:
- Implementar nova feature do roadmap
- Corrigir bugs reportados
- Escrever testes
- Otimizar performance
- Documentar código

### 🎨 Design & UX
- **UI/UX**: Desenhos de interfaces, protótipos
- **Acessibilidade**: Auditorias, fixes de WCAG
- **Branding**: Logo, cores, identidade visual

**Exemplos de tasks**:
- Design de telas
- Auditoria de acessibilidade
- Criação de design system
- Melhorias visuais

### 📝 Documentação
- **README** e guias
- **API docs** e exemplos
- **Tutorials** e how-to guides
- **Traducções** para outros idiomas

**Exemplos de tasks**:
- Escrever guia de setup
- Criar tutoriais em vídeo
- Traduzir documentação
- Melhorar explicações

### 🌍 Comunidade
- **Feedback** sobre features
- **Advocacy** - Compartilhe o projeto
- **Mentorship** - Ajude novos contribuidores
- **Testing** - Use e reporte feedback

**Exemplos de tasks**:
- Testar features em staging
- Sugerir features
- Responder issues
- Organizar events

### ♿ Acessibilidade
- **Auditorias WCAG**
- **Testes com leitores de tela**
- **Consultoria** sobre boas práticas
- **Validação** com comunidade de pessoas com deficiência

---

## 🚀 Como Começar

### 1️⃣ Setup de Desenvolvimento

```bash
# Clone o repositório
git clone https://github.com/rubeduardo/accesshub.git
cd accesshub

# Instale as dependências
npm install  # ou pip install -r requirements.txt

# Configure o ambiente
cp .env.example .env.local

# Inicie o desenvolvimento
npm run dev
```

[Veja SETUP.md para instruções detalhadas →](docs/SETUP.md)

### 2️⃣ Encontre uma Tarefa

1. **Procure [issues com label `good-first-issue`](../../issues?q=label%3Agood-first-issue)** - Ideais para iniciantes
2. **Procure [issues com label `help-wanted`](../../issues?q=label%3Ahelp-wanted)** - Tarefas que precisam de ajuda
3. **[Veja o Roadmap](ROADMAP.md)** - Tasks planejadas
4. **[Abra uma discussão](../../discussions)** - Sugira uma tarefa

### 3️⃣ Comunique Sua Intenção

Antes de começar:
- Comente na issue: "_Gostaria de trabalhar nisto_"
- Descreva brevemente sua abordagem
- Pergunte se tiver dúvidas

### 4️⃣ Crie um Fork e Branch

```bash
# Faça fork (via GitHub)
# Clone seu fork
git clone https://github.com/SEU_USERNAME/accesshub.git
cd accesshub

# Crie uma branch para sua feature
git checkout -b feature/sua-feature
# ou para bugs:
git checkout -b fix/seu-bug
```

### 5️⃣ Faça Suas Mudanças

- Escreva código claro e bem documentado
- Siga as convenções do projeto
- Adicione testes
- Teste localmente

### 6️⃣ Commit com Conventional Commits

```bash
# Feature
git commit -m "feat: adiciona validação de QR Code"

# Bug fix
git commit -m "fix: corrige erro de validação"

# Documentation
git commit -m "docs: melhora guia de setup"

# Tests
git commit -m "test: adiciona testes para validação"

# Refactor
git commit -m "refactor: melhora estrutura de pastas"
```

[Aprenda Conventional Commits →](https://www.conventionalcommits.org/pt-br/)

### 7️⃣ Push e Abra um Pull Request

```bash
# Push para seu fork
git push origin feature/sua-feature

# Abra um PR no GitHub
# Use o template fornecido
# Descreva o que você fez e por quê
```

**Template de PR**:
```markdown
## Descrição
Breve descrição do que foi feito

## Tipo de Mudança
- [ ] Nova feature
- [ ] Bug fix
- [ ] Breaking change
- [ ] Documentação

## Como testar
Passos para validar a mudança

## Checklist
- [ ] Testes adicionados
- [ ] Documentação atualizada
- [ ] Sem warnings/errors de lint
```

### 8️⃣ Code Review

- Responda aos feedbacks
- Faça ajustes se solicitado
- Aproveite para aprender!

### 9️⃣ Celebre! 🎉

Seu PR foi merged! Você agora é um contribuidor do AccessHub!

---

## 📋 Padrões de Código

### Convenções de Commit (Conventional Commits)

```
<tipo>(<escopo>): <descrição>

<corpo>

<rodapé>
```

**Tipos**:
- `feat`: Nova feature
- `fix`: Correção de bug
- `docs`: Mudanças em documentação
- `style`: Formatação, sem mudança lógica
- `refactor`: Refatoração
- `perf`: Melhorias de performance
- `test`: Testes
- `chore`: Dependências, config

**Exemplos**:
```
feat(auth): adiciona autenticação JWT
fix(qrcode): corrige erro de geração de QR
docs: melhora README
test(associados): adiciona testes de cadastro
```

### Padrões de Código

#### Python (FastAPI)

```python
# Use type hints
def criar_associado(nome: str, email: str) -> Associado:
    """Cria um novo associado.
    
    Args:
        nome: Nome completo
        email: Email válido
        
    Returns:
        Objeto Associado criado
        
    Raises:
        ValueError: Se email inválido
    """
    # implementação
```

#### TypeScript (Next.js)

```typescript
// Use tipos explícitos
interface Associado {
  id: string;
  nome: string;
  email: string;
  createdAt: Date;
}

export async function criarAssociado(
  nome: string,
  email: string
): Promise<Associado> {
  // implementação
}
```

### Geral

- **Nomes descritivos**: `criarAssociado` não `criar()`
- **Comentários úteis**: Explique "por quê", não "o quê"
- **DRY**: Don't Repeat Yourself
- **SOLID**: Princípios de design
- **Testes**: Teste seu código

---

## 🧪 Testes

Todas as contribuições devem incluir testes!

### Frontend (React/TypeScript)

```bash
# Rode testes
npm run test

# Com cobertura
npm run test:coverage
```

```typescript
import { render, screen } from '@testing-library/react';
import { CarteirinhaDigital } from './CarteirinhaDigital';

describe('CarteirinhaDigital', () => {
  it('deve exibir ID do associado', () => {
    render(<CarteirinhaDigital id="123" nome="João" />);
    expect(screen.getByText('123')).toBeInTheDocument();
  });
});
```

### Backend (Python/FastAPI)

```bash
# Rode testes
pytest

# Com cobertura
pytest --cov
```

```python
from fastapi.testclient import TestClient
from main import app

client = TestClient(app)

def test_criar_associado():
    response = client.post(
        "/api/associados",
        json={"nome": "João", "email": "joao@example.com"}
    )
    assert response.status_code == 201
    assert response.json()["nome"] == "João"
```

---

## ♿ Acessibilidade

Acessibilidade é uma prioridade! Ao contribuir:

### Frontend

- ✅ Use elementos semânticos (`<button>` não `<div>`)
- ✅ Adicione `alt` em imagens
- ✅ Use cores com contraste suficiente
- ✅ Teste com teclado (Tab, Enter, Escape)
- ✅ Teste com leitor de tela (NVDA, JAWS, VoiceOver)

```html
<!-- ✅ Bom -->
<button aria-label="Validar carteirinha">
  <CheckIcon />
</button>

<!-- ❌ Ruim -->
<div onClick={validar}>Validate</div>
```

### Backend

- ✅ Validação clara de inputs
- ✅ Mensagens de erro específicas
- ✅ Documentação clara da API

---

## 📝 Documentação

Toda feature deve vir com documentação!

### Código

```typescript
/**
 * Valida um QR Code de carteirinha
 * @param qrData - String do QR Code
 * @returns Objeto com dados do associado ou null se inválido
 * @throws Error se QR Code corrompido
 * 
 * @example
 * const resultado = await validarQRCode('QR123');
 * if (resultado) {
 *   console.log(resultado.nome);
 * }
 */
```

### README de Feature

Crie um `README.md` na pasta da feature:

```markdown
# Feature Name

## O que faz
Descrição breve

## Como usar
Exemplos de uso

## Configuração
Se precisa de config especial

## Testes
Como testar
```

---

## 🔍 Checklist Antes de Fazer PR

- [ ] Li o README
- [ ] Li o CONTRIBUTING.md
- [ ] Criei uma branch com nome descritivo
- [ ] Meu código segue os padrões do projeto
- [ ] Adicionei testes
- [ ] Rodei testes localmente (100% passing)
- [ ] Documentei meu código
- [ ] Atualizei documentação externa se necessário
- [ ] Meu commit segue Conventional Commits
- [ ] Verifiquei acessibilidade (se frontend)

---

## ❌ O Que Evitar

- ❌ Rebase no main sem avisar mantedores
- ❌ Commits gigantescos (divida em partes lógicas)
- ❌ Código sem testes
- ❌ Comentários spam ou desrespeitosos
- ❌ Features grandes sem discussão prévia
- ❌ Ignorar feedback do code review

---

## 🐛 Reportando Bugs

Encontrou um bug? Abra uma issue!

### Título Descritivo
```
❌ "Erro de validação"
✅ "QR Code não valida carteirinha expirada"
```

### Descrição

```markdown
## Descrição do bug
[Descrição clara e concisa]

## Como reproduzir
1. Vá para a página...
2. Clique em...
3. Observe o erro...

## Comportamento esperado
[O que deveria acontecer]

## Comportamento atual
[O que está acontecendo]

## Screenshots
[Se aplicável]

## Ambiente
- OS: [Windows/Linux/Mac]
- Browser: [Chrome/Firefox/Safari]
- Versão: [v0.1]
```

---

## 💡 Sugerindo Features

Quer sugerir uma nova feature?

1. **[Procure se já existe](../../issues)** - Talvez alguém tenha sugerido antes
2. **[Abra uma discussão](../../discussions)** - Compartilhe sua ideia
3. **Gather feedback** - Veja o que a comunidade acha
4. **[Abra uma issue](../../issues)** - Com a feature bem definida

### Template de Feature

```markdown
## Descrição
[Descrição clara da feature]

## Problema que resolve
[Qual problema específico resolve?]

## Solução proposta
[Como implementar?]

## Alternativas consideradas
[Outras formas de resolver?]

## Contexto adicional
[Exemplos, links, mockups]
```

---

## 🤔 FAQ

### Preciso ter experiência para contribuir?
**Não!** Temos issues marcadas `good-first-issue` especialmente para iniciantes. Aprenda enquanto contribui!

### Como me comunicar com a equipe?
- **Issues** - Para tarefas e bugs
- **Discussões** - Para ideias e feedback
- **Pull Requests** - Para código

### Qual é a política de commit?
Siga Conventional Commits. Veja exemplos acima.

### Meu PR foi rejeitado, e agora?
Não é rejeição pessoal! Code review é para manter qualidade. Leia feedback e tente novamente.

### Posso contribuir com documentação em outro idioma?
**Sim!** Translações são muito bem-vindas.

### Quanto tempo leva para revisar meu PR?
Normalmente 2-3 dias úteis. Somos voluntários, mas levamos a sério!

### Preciso assinar um CLA?
Não. Apenas escolha uma licença compatível com MIT.

---

## 🌟 Créditos

Contribuidores são listados em:
- README.md (seção Contributors)
- [GitHub Insights](../../pulse)

---

## 📞 Precisa de Ajuda?

- 🐙 Abra uma [discussão](../../discussions)
- 📧 Comente em issues
- 💬 Nos encontre no GitHub

---

## 📖 Recursos Úteis

- [Como usar Git](https://git-scm.com/book/pt-BR/v2)
- [Conventional Commits](https://www.conventionalcommits.org/pt-br/)
- [WCAG 2.1 Accessibility](https://www.w3.org/WAI/WCAG21/quickref/)
- [React Best Practices](https://react.dev/)
- [FastAPI Tutorial](https://fastapi.tiangolo.com/)

---

## ❤️ Código de Conduta

Por favor leia nosso [Código de Conduta](CODE_OF_CONDUCT.md).

TL;DR: Seja respeitoso, inclusivo e acolhedor com todos.

---

**Obrigado por nos ajudar a tornar AccessHub melhor! 🙌**

*"Acessibilidade é direito, não luxo"*
