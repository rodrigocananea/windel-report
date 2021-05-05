*Servidor*

Passo 1:

Certificar com todos os usuários(Vendedores) que utilizam o App Mobile se eles não possuem pedidos pendentes de envio, com o status (Aguardando Replicação ou em Criação), pois os mesmos serão perdidos.
Verificar se os pedidos (Aguardando Replicação) foram sincronizados e aparecem no sistema (MOB001). 

Passo 2:
Orientar ao cliente para encerrar o sistema em todos os computadores e não acessar até finalizar o processo.

Passo 3:
Parar o seguinte serviço:
*Firebird*

Passo 4:
Desinstalar o serviço (Windel Sincronizador)

Passo 5:
Realizar a cópia de segurança do banco de dados.
Renomear o banco de dados para ex.: SISTEMA.FDB para SISTEMA1.FDB
Ajustar o arquivo Local.cfg aplicando o mesmo nome utilizado acima.
Iniciar o serviço do Firebird.
Atualizar o sistema.
OBS.: Somente para caso onde a versão seja inferior a 7.3.5.0.

Passo 6:
Acessar o editor SQL e executar os sequintes scripts:
*Script 1:*
DELETE FROM REPLIC_CONFIG
*Script 2:*
DELETE FROM MOBILE_PEDIDO_PRODUTOS
WHERE IDPEDIDO NOT IN (SELECT IDPEDIDO FROM MOBILE_PEDIDO)
*Script 3:*
DELETE FROM REPLIC_DATA_STATUS
Fechar o sistema.

Passo 7:
Abrir o sistema.
Acessar o editor SQL e executar o sequinte script.
DELETE FROM REPLIC_DATA_STATUS
Obs.: Pode demorar para realizar a exclusão da tabela.
Fechar o sistema.

Passo 8:
Realizar o download do novo sincronizador disponível no link:
http://suporte.windel.com.br/alf/sincronizador.zip
Extrair o conteúdo na raiz da pasta Windel.
Executar como administrador o arquivo Sincronizador.exe
Aguardar realizar o processo, que estará concluído quando aparecer a mensagem (Pronto para Instalar).
Fechar a janela.

Passo 9:
Parar o serviço do Firebird.
Renomear o banco de dados para ex.: SISTEMA1.FDB para SISTEMA.FDB
Ajustar o arquivo Local.cfg aplicando o mesmo nome utilizado acima.
Iniciar o serviço do Firebird.
Instalar como administrador o serviço do sincronizador (sincronizador-install)
Acessar o sistema e liberar o acesso aos terminais.



*Dispositivos*
Desinstalar a antiga versão do App Mobile.
Instalar a nova versão disponível no link.
https://play.google.com/store/apps/details?id=br.com.windel.mobile
Fazer o acesso do App.
Realizar as parametrizações do app (Configurações e Sincronizar)
Configurações:
Sincronização automática = Sim
Período = Minuto
Intervalo de Execução = A cada 1 minutos

Sincronizar:
Sincronização auto. (todos)= Sim
Forçar a sincronização.

Aguardar realizar a sincronização dos dados.

*Finalização*
Emitir um pedido de testes.
Aguardar a sincronização.
Acessar o MOB001 e certificar se o pedido foi sincronizado.