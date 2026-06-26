# Acessibilidade no AccessHub

## Compromisso

AccessHub está comprometido em ser uma plataforma totalmente acessível, seguindo as Diretrizes de Acessibilidade para Conteúdo Web (WCAG) 2.1 nível AA.

## Padrões

Nos comprometemos a seguir:

- **WCAG 2.1 Level AA**: Padrão mínimo para todas as interfaces
- **ARIA**: Atributos semânticos apropriados
- **Keyboard Navigation**: Navegação completa via teclado
- **Screen Reader Support**: Compatibilidade total

## Checklist de Acessibilidade

### Estrutura
- [ ] Marcação semântica HTML
- [ ] Hierarquia de headings apropriada
- [ ] Landmarks ARIA
- [ ] Roles e labels ARIA quando necessário

### Visual
- [ ] Contraste de cores ≥ 4.5:1 para texto
- [ ] Sem dependência de cor apenas
- [ ] Texto dimensionável até 200%
- [ ] Suporte a modo escuro

### Interatividade
- [ ] Navegação por teclado completa
- [ ] Indicador de foco visível
- [ ] Sem traps de teclado
- [ ] Timeouts avisos

### Conteúdo
- [ ] Descrições de imagens (alt text)
- [ ] Captions para vídeos
- [ ] Transcrições de áudio
- [ ] Linguagem clara e simples

## Testes

Realizamos testes de acessibilidade regularmente:

- Testes automatizados com Axe, Lighthouse
- Testes com usuários reais
- Testes com leitores de tela (NVDA, JAWS, VoiceOver)
- Testes com navegação por teclado

## Relatório de Problemas

Se encontrar um problema de acessibilidade, por favor:

1. Verifique se já foi reportado
2. Crie uma issue com tag `accessibility`
3. Descreva o problema e o impacto
4. Inclua screenshot/vídeo se possível
