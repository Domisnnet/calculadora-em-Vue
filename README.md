#🧮✨ - Uma Calculadora com o Poder Reativo do Vue.js

Cansado de calculadoras sem graça? Prepare-se para conhecer a **Vue-Calc**, uma aplicação web que não apenas calcula, mas faz isso com estilo, reatividade e a elegância do **Vue.js**.

Este projeto é mais do que apenas código: é um playground para demonstrar conceitos essenciais de desenvolvimento front-end de uma forma divertida e visual.

### Veja em Ação!

*(Dica: Grave um GIF rápido da sua calculadora funcionando e substitua o link abaixo. Ferramentas como [LICEcap](https://www.cockos.com/licecap/) ou [Giphy Capture](https://giphy.com/apps/giphycapture) são ótimas para isso!)*

![Demo da Calculadora](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExd2Jna3R0aXZpZmEzeWw4cGprOHBia2tldDJxdHh5MTR5Nmd0aXFzZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o7btPCcdNni1e3Sj6/giphy.gif)

---

### 🗺️ **Navegação Rápida**
*   [🚀 Superpoderes](#-superpoderes-features)
*   [⚙️ Caixa de Ferramentas](#️-nossa-caixa-de-ferramentas-tecnologias)
*   [🧠 Mergulho no Código](#-mergulho-no-cérebro-da-calculadora)
*   [👨‍💻 Como Rodar na sua Máquina](#-colocando-a-mão-na-massa-setup)
*   [💡 Missão: Próximos Níveis!](#-missão-próximos-níveis-sugestões)
*   [🤝 Faça Parte](#-faça-parte-desta-jornada)

---

## 🚀 Superpoderes (Features)

Esta não é a calculadora da sua avó (a menos que sua avó seja uma dev descolada).

*   ✅ **Operações Clássicas:** Soma, Subtração, Multiplicação e Divisão com precisão.
*   🧠 **Cálculos em Cadeia:** Faça `10 + 5 * 2` e veja a mágica acontecer. A calculadora sabe a ordem!
*   🎨 **Design Minimalista com CSS Grid:** Uma interface limpa, organizada e construída com uma das ferramentas mais poderosas do CSS moderno.
*   ⚡ **Reatividade Instantânea:** Cada clique, cada número, cada operação... tudo é refletido na tela em tempo real, graças ao Vue.js.
*   🔄 **Reset Total (AC):** Errou tudo? Sem problemas! O botão `AC` é seu melhor amigo para começar do zero.

## ⚙️ Nossa Caixa de Ferramentas (Tecnologias)

Para construir algo legal, usamos ferramentas legais.

*   **[Vue.js](https://vuejs.org/)**: O coração pulsante do projeto, gerenciando o estado e a reatividade da interface.
*   **JavaScript (ES6+)**: O cérebro por trás de toda a lógica de cálculo.
*   **HTML5**: O esqueleto que estrutura nossos componentes.
*   **CSS3 (Grid Layout)**: A maquiagem que deixa tudo bonito e perfeitamente alinhado.

## 🧠 Mergulho no Cérebro da Calculadora

Quer espiar por baixo do capô? A mágica acontece no `state` e nos `methods` do componente `Calculator.vue`.

```javascript
// ...dentro do export default
export default {
    data() {
        return {
            displayValue: '0',   // O que aparece no visor. Simples assim.
            clearDisplay: false, // Flag mágica para saber se o próximo dígito limpa o visor.
            operation: null,     // Guarda o operador: +, -, *, /
            values: [0, 0],      // Nosso cérebro: [primeiro_valor, segundo_valor]
            current: 0,          // Aponta para qual 'value' estamos alterando (0 ou 1).
        };
    },
    methods: {
        // Reseta tudo para o estado inicial. A forma mais elegante de "começar de novo".
        clearMemory() {
            Object.assign(this.$data, this.$options.data());
        },

        // Adiciona um dígito ao visor e atualiza o estado.
        addDigit(n) {
            // Lógica inteligente para não permitir múltiplos pontos (ex: "5.4.3")
            if (n === '.' && this.displayValue.includes('.')) {
                return;
            }

            // O visor deve ser limpo? Ou o valor atual é '0'? Então começamos um novo número.
            const shouldClearDisplay = this.displayValue === '0' || this.clearDisplay;
            const currentValue = shouldClearDisplay ? '' : this.displayValue;
            this.displayValue = currentValue + n;
            this.clearDisplay = false;

            // Atualiza o valor correspondente no nosso "cérebro" (o array 'values')
            this.values[this.current] = parseFloat(this.displayValue);
        },

        // Define a operação e prepara para o próximo número. É aqui que os cálculos acontecem!
        setOperation(operation) {
            // ... a lógica de cálculo principal reside aqui.
        }
    }
}
```

> **Nota de Curiosidade:** A função `eval()` é usada para o cálculo. É uma solução rápida e eficaz para este projeto, mas em um ambiente de produção, seria substituída por uma função de análise de expressão matemática para maior segurança!

## 👨‍💻 Colocando a Mão na Massa (Setup)

Pronto para rodar o projeto e talvez... melhorá-lo?

1.  **Clone este universo:**
    ```bash
    git clone https://github.com/seu-usuario/seu-repositorio.git
    ```

2.  **Entre na nave:**
    ```bash
    cd seu-repositorio
    ```

3.  **Instale os propulsores:**
    ```bash
    npm install
    ```

4.  **Ligue os motores (inicie o servidor):**
    ```bash
    npm run serve
    ```
5.  Abra seu navegador e voe para `http://localhost:8080`! 🚀

## 💡 Missão: Próximos Níveis! (Sugestões)

Acha que pode deixar a Vue-Calc ainda mais incrível? Aqui estão algumas missões para você:

-   [ ] **Modo Noturno:** Adicionar um botão para alternar entre temas claro e escuro.
-   [ ] **Suporte a Teclado:** Permitir que os usuários digitem os números e operações pelo teclado.
-   [ ] **Histórico de Cálculos:** Exibir uma lista das últimas operações realizadas.
-   [ ] **Novos Poderes:** Implementar funções como porcentagem (`%`), raiz quadrada (`√`) e potência (`x²`).
-   [ ] **Animações Cinéticas:** Adicionar micro-animações nos botões ao clicar.

## 🤝 Faça Parte Desta Jornada

Encontrou um bug? Tem uma ideia genial para uma nova feature? Sinta-se em casa!

1.  Dê um **Fork** no projeto.
2.  Crie uma nova **Branch** (`git checkout -b feature/sua-feature-incrivel`).
3.  Faça suas alterações e **Commit** (`git commit -m 'Adiciona feature incrível'`).
4.  Dê um **Push** para a Branch (`git push origin feature/sua-feature-incrivel`).
5.  Abra um **Pull Request**.

Qualquer contribuição é super bem-vinda!

---

**Feito com paixão, código e muito café ☕**