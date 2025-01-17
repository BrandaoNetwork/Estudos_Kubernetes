
# Composição do Agendamento do CronJob

Esta tabela explica a composição de um agendamento no formato **cron** usado nos **CronJobs** do Kubernetes.

## Composição da Expressão Cron

| **Campo**        | **Valor Aceito**          | **Descrição**                                                                            | **Exemplo**            |
|-------------------|---------------------------|-----------------------------------------------------------------------------------------|-------------------------|
| **Minutos (m)**   | `0-59`                   | Define o minuto do início da execução.                                                 | `0` → No início da hora. |
| **Horas (h)**     | `0-23`                   | Define a hora do início da execução (base 24h).                                         | `3` → Às 3h da manhã.    |
| **Dia do mês (dom)** | `1-31`                | Define o dia do mês para execução.                                                     | `15` → No dia 15.        |
| **Mês (mon)**     | `1-12` ou abreviações: `jan`, `feb`, ... | Define o mês para execução.                                    | `7` ou `jul` → Julho.    |
| **Dia da semana (dow)** | `0-6` ou abreviações: `sun`, `mon`, ... | Define o dia da semana para execução (0 = domingo).               | `1` ou `mon` → Segunda-feira. |
| **Comando**       | N/A                      | Não faz parte da sintaxe cron do Kubernetes, mas define o que será executado no Job.    | N/A                     |

---

## Operadores e Combinações Especiais

| **Operador/Comando** | **Descrição**                                                                                 | **Exemplo**                             |
|-----------------------|---------------------------------------------------------------------------------------------|-----------------------------------------|
| `*`                  | Executa em todos os valores possíveis do campo.                                              | `* * * * *` → Executa a cada minuto.    |
| `,`                  | Lista de valores específicos.                                                                | `5,10` → Nos minutos 5 e 10.            |
| `-`                  | Intervalo de valores.                                                                        | `1-5` → De 1 a 5.                       |
| `/`                  | Passo: executa em intervalos regulares.                                                      | `*/15` → A cada 15 minutos.             |
| `?`                  | Ignora valores no campo **dia do mês** ou **dia da semana** (útil para evitar conflitos).     | `0 9 1 * ?` → Todo dia 1 às 9h.         |
| `@yearly`            | Especial: Executa uma vez ao ano (`0 0 1 1 *`).                                              | `@yearly` → Meia-noite de 1º de janeiro. |
| `@monthly`           | Especial: Executa uma vez ao mês (`0 0 1 * *`).                                              | `@monthly` → Meia-noite no 1º dia do mês.|
| `@weekly`            | Especial: Executa uma vez por semana (`0 0 * * 0`).                                          | `@weekly` → Meia-noite de domingo.      |
| `@daily`             | Especial: Executa uma vez por dia (`0 0 * * *`).                                             | `@daily` → Meia-noite todos os dias.    |
| `@hourly`            | Especial: Executa uma vez por hora (`0 * * * *`).                                            | `@hourly` → Todo início de hora.        |

---

## Exemplos de Agendamentos

| **Expressão**    | **Descrição**                                    |
|-------------------|------------------------------------------------|
| `0 3 * * *`      | Todos os dias às 3h.                            |
| `*/15 8-18 * * 1-5` | A cada 15 minutos, das 8h às 18h, de segunda a sexta-feira. |
| `0 0 1 1 *`      | Meia-noite do dia 1º de janeiro.                |
| `30 6 1 * 0`     | Todo primeiro domingo do mês às 6h30.           |
| `0 12 * * 0`     | Todo domingo ao meio-dia.                       |

---

Se precisar de ajuda para criar ou revisar uma expressão cron específica, é só pedir! 😊
