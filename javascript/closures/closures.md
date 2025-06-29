### 📚 Closures

- **Conceito**
  <p style="margin-bottom: 15px;">Uma closure é uma função interna que está inserida dentro de uma função externa, e que possuí acesso às variáveis e métodos da função pai, mesmo após o tempo de execução.</p>

  ```js
  const createAgePermissionChecker = (minAge, action) => {
    return (age) => {
      if (age < minAge) {
        return `Você não tem ${minAge} anos ou mais. Portanto, não está permitido para ${action}.`;
      } else {
        return `Você pode ${action}.`;
      }
    };
  };

  const canDriveInBrazil = createAgePermissionChecker(18, 'dirigir');
  const canDriveInUS = createAgePermissionChecker(16, 'dirigir');
  const canVote = createAgePermissionChecker(16, 'votar');
  const canRideMotorcycle = createAgePermissionChecker(10, 'andar de moto');

  console.log(canDriveInBrazil(20));
  // Você pode dirigir.
  console.log(canDriveInBrazil(15));
  // Você não tem 18 anos ou mais. Portanto, não está permitido para dirigir.
  console.log(canDriveInUS(17));
  // Você pode dirigir.
  ```

- **Como aplicar na prática**

  - Criar funções que retornam outras funções, usar para encapsulamento.

- **Quando usar**

  - Quando precisa manter um estado privado entre chamadas.
  - Para criar funções com dados parcialmente fixos.
  - Em funções geradoras de comportamento (ex: factories).

- **Por que usar**

  - Encapsulamento e manutenção de estado sem usar classes.
  - Redução de código repetido.
  - Funções mais flexíveis e reutilizáveis.

- **Limitações e desvantagens**

  - Pode dificultar a leitura do código se mal utilizado.
  - Possível consumo de memória se mantiverem referências não utilizadas (risco de _memory leaks_ em alguns contextos).

- **Erros comuns**

  - Não entender que o valor capturado é o _objeto_, não o valor na hora de execução.
  - Esperar que a variável seja "congelada" no momento da criação (quando na verdade pode mudar se referenciar um mesmo objeto mutável).
  - Confusão com escopo (ex: tentar acessar variáveis que não existem mais).

- **Variações e alternativas**

  - Uso de classes com atributos privados.

- **Como funciona por dentro (opcional, mas útil)**

  - A closure mantém uma referência ao _ambiente léxico_ da função.

- **Melhores práticas**

  - Usar nomes claros para funções internas.
  - Evitar closures complexas em contexto sem necessidade.

- **Como integrar com projetos reais**
  - Criar contadores, fábricas de funções, filtros personalizados.
  - Encapsular lógica de validação ou controle de acesso.
