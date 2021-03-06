# CADASTROS DE CLIENTES
Esse relatório exibe de forma simples os titulos de contas a receber e contas a pagar realizando um agrupamento dos pagamentos pela forma de pagamento utilizada no momento da baixa

**Baixar** [Cadastros de Clientes](https://github.com/rodrigocananea/windel-report/raw/main/FINANCEIRO/TITULOS_SIMPLIFICADO/titulos_simplificado.zip)

#### Script SQL
````sql
SELECT T.IDTITULO,
T.IDPARCELA,
T.NOMECLIFOR,
PG.FORMAPAG AS TIPOPAG,
F.DESCRICAO,
T.VENCIMENTO,
T.VALOR,
T.DTPAGAMENTO
FROM TITULOS T
LEFT JOIN PAGAMENTOS PG ON T.IDEMPRESA = PG.IDEMPRESA AND T.IDCLIFOR = PG.IDCLIFOR
AND T.IDTITULO = PG.IDTITULO AND T.IDSERIE = PG.IDSERIE AND T.IDPARCELA = PG.IDPARCELA
AND T.IDTIPO = PG.IDTIPO
LEFT JOIN FORMAPGTO F ON PG.FORMAPAG = F.IDFORMAPGTO
WHERE T.IDEMPRESA = :EMPRESA
AND T.IDTIPO = :TIPO
AND T.DTPAGAMENTO BETWEEN :DE AND :ATE
AND T.SITUACAO IN(:SITUACAO)
GROUP BY 4,5,6,1,2,3,8,7
ORDER BY PG.FORMAPAG, T.VENCIMENTO, T.IDPARCELA, T.IDTITULO

````

### ***Exemplo GIF***

<p align="center">
 <img src="https://github.com/rodrigocananea/windel-report/blob/main/FINANCEIRO/TITULOS_SIMPLIFICADO/titulos_simplificado.gif" />
</p>
