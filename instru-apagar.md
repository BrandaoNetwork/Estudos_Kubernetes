# Configuração do OpenTelemetry no Jenkins

## Problema
Ao acessar a tela **Stage View** no Jenkins, aparece a seguinte mensagem no final da página:

```
Please define an OpenTelemetry Visualisation URL of pipelines in Jenkins configuration
```

Essa mensagem indica que o Jenkins não sabe para onde apontar as visualizações OpenTelemetry dos pipelines, pois a configuração da **OpenTelemetry Visualisation URL** não foi definida.

## Solução

### 1️⃣ Verificar se o plugin OpenTelemetry está instalado
1. No Jenkins, vá em **Manage Jenkins** > **Plugin Manager** > **Installed**.
2. Verifique se o plugin **"OpenTelemetry"** está instalado.
3. Se não estiver, instale-o e reinicie o Jenkins.

### 2️⃣ Configurar a URL de visualização do OpenTelemetry no Jenkins
1. Acesse **Manage Jenkins** > **Configure System**.
2. Role para baixo até encontrar a seção **OpenTelemetry**.
3. Na opção **OpenTelemetry Visualisation URL**, defina o endpoint da ferramenta onde você está coletando as métricas do OpenTelemetry.
   - Exemplos de URLs para ferramentas populares:
     - **Jaeger**: `http://jaeger.mycompany.com/`
     - **Grafana Tempo**: `http://grafana.mycompany.com/explore`
     - **Datadog APM**: `https://app.datadoghq.com/apm`
4. Salve as configurações.

## Considerações para Implementação
Como a migração para OpenTelemetry está sendo feita sem impactar o monitoramento atual via **Datadog**, algumas recomendações:
- Se ainda não estiver coletando os spans do Jenkins, configure um **OpenTelemetry Collector** para rotear as informações.
- Se o Jenkins ainda não está enviando dados, configure os **tracers no Jenkinsfile** ou nas configurações globais.
- Certifique-se de que a ferramenta escolhida para visualização já está recebendo os spans corretamente antes de configurar a URL.

Se precisar de mais detalhes ou suporte para configurar algo específico, entre em contato! 🚀
