Regressão Linear na Prática com R

Este repositório contém um projeto prático de Regressão Linear usando a linguagem R. O objetivo é fornecer uma visão clara e acessível sobre como implementar modelos de regressão linear para análise de dados e predição de resultados.

		Conteúdo

 Neste projeto, você encontrará:

.Introdução à Regressão Linear: Conceitos básicos e fundamentos.
.Preparação e Visualização de Dados: Carregamento, visualização e sumarização dos dados.
.Correlação: Análise da correlação entre variáveis.
.Modelo de Regressão Logística: Construção e interpretação de modelos.
.Avaliação do Modelo: Comparação do modelo com os dados reais e avaliação de desempenho.
.Predição: Teste do modelo com novos dados.

Código R

1.Carga de Dados

r
eleicao = read.csv("Eleicao.csv", sep=';', header=T)
eleicao

2.Gráfico e Visualização

r
plot(eleicao$DESPESAS, eleicao$SITUACAO)
summary(eleicao)

3.Correlação

r
Copiar código
cor(eleicao$DESPESAS, eleicao$SITUACAO)

4.Modelo de Regressão Logística

r
Copiar código
modelo = glm(SITUACAO ~ DESPESAS, data=eleicao, family="binomial") 
summary(modelo)

5.Modelo Comparado aos Dados

r
plot(eleicao$DESPESAS, eleicao$SITUACAO, col='red', pch=20)
points(eleicao$DESPESAS, modelo$fitted, pch=4)

6.Testar o Modelo com os Próprios Candidatos

r
prever = predict(modelo, newdata=eleicao, type="response")
prever = prever >= 0.5
prever

7.Avaliar Performance
r
confusao = table(prever, eleicao$SITUACAO)
confusao
taxaacerto = (confusao[1] + confusao[4]) / sum(confusao)
taxaacerto

8.Novos Candidatos
r
prevereleicao = read.csv("NovosCandidatos.csv", sep=';', header=T)
prevereleicao

9.Previsão
r
prevereleicao$RESULT = predict(modelo, newdata=prevereleicao, type="response")
prevereleicao$RESULT
prevereleicao$RESULT >= 0.5

Contribuição

Sinta-se à vontade para contribuir com sugestões, melhorias ou correções. Toda ajuda é bem-vinda!

-------------------------------------------------------------------------------------------------------------------------------------------
Espero que este projeto seja útil para você. Se tiver alguma dúvida ou sugestão, não hesite em abrir uma issue ou entrar em contato.
------------------------------------------------------------------------------------------------------------------------------------------
Esse repositório está pronto para ser utilizado e explorado. Se precisar de alguma alteração ou tiver mais alguma informação para adicionar, por favor, me avise!


