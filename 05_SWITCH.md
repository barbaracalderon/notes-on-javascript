# EN: Switch

If you have multiple `if/else` statements to compare for **one value**, it may be a good idea to use a switch.

Here's the structure example.

```javascript
const day = "monday";

switch (day) {
  case "monday":
    console.log("Plan course structure.");
    console.log("Go to coding meetup.");
    break;
  case "tuesday":
    console.log("Prepare theory videos.");
    break;
  case "wednesday":
  case "thursday":
    console.log("Write code examples.");
    break;
  case "friday":
    console.log("Record videos!");
    break;
  case "saturday":
  case "sunday":
    console.log("Enjoy the weekend :D");
    break;
  default:
    console.log("Error: not a valid day!");
}
```

---

# PT: Switch

Se você tem múltiplos `if/else` para comparar com **um valor**, talvez seja boa ideia usar um switch.

Estrutura de exemplo abaixo.

```javascript
const dia = "segunda";

switch (dia) {
  case "segunda":
    console.log("Planejar estrutura do curso.");
    console.log("Ir para o meetup.");
    break;
  case "terça":
    console.log("Preparar vídeos teóricos.");
    break;
  case "quarta":
  case "quinta":
    console.log("Escrever códigos de exemplo.");
    break;
  case "sexta":
    console.log("Gravar vídeos!");
    break;
  case "sábado":
  case "domingo":
    console.log("Aproveitar o final-de-semana :D");
    break;
  default:
    console.log("Error: dia não é válido!");
}
```
