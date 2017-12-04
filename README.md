# Tutorial-SED
Alguns exemplos do uso do comando (Linguagem) SED...


Mais exemplos sed 
*****************

Formato:


sed 'Ys///X' nome_arq
	Y = número da linha (se omitido é = todas).
	X = número da ocorrência em cada linha.



--- Substitui apenas na primeira linha:

	sed '1s/,/ /g' contatos


--- Substitui apenas na última linha:

	sed '$s/,/ /g' contatos 


--- Subtitui apenas primeira ocorrencia de cada linha:

	sed 's/,/ /1' contatos 

	sed 's/,/ /' contatos  #(tb o mesmo! Se omite o núm)


--- Retira varias vírgulas para apenas uma:

	sed -r 's/(,)+/,/g' contactos.csv 

  Resultado:
  Colombe,,,,,,,,
  Colombe,


--- Substitui apenas entre as linhas 3 e 6:

	sed  '3,6s/dia/noite/'


--- Substitui apenas nas linhas que contém a palavra "terceiro":

	sed '/terceiro/s/dia/noite/g'


--- NÄO substitui nas linhas onde aparece a palavra "terceiro":

	sed '/terceiro/!s/dia/noite/g'




--- Imprime determinada linha:

	sed -n '2p' contatos 	--- Linha 2

--- Imprime a primeira linha:

	sed -n '1p' contatos

--- Imprime a última linha:

	sed -n '$p' contatos

--- Imprime de N° linha até a X° linha:

	sed -n '1,7p' contatos

--- Imprime da N° linha até o final:

	sed -n '5,$p' contatos


--- Imprime de tantas em tantas linhas:
	seq 10 | 
	sed -n '1~2p'	--- Linhas ímpares
	seq 10 | 
	sed -n '2~2p'	--- Linhas pares
	seq 70 | 
	sed -n '0~7p'	--- Somentes as múltiplas de 7


--- Imprime somente as linhas que contém um padräo:

	sed -n '/jose/p' contatos	--- Näo funciona

	sed -n '/jose/Ip' contatos	--- Agora tem I-nsensive Case

	sed -n '/Jose/!p' contatos	--- Excluindo as que têm o padräo.


--- Imprime as linhas que contenham padrao1 OU padrao2:

	sed -n '/jose\|casa/Ip' contatos	--- Imprime linhas que contenham a palavra "jose" (Insensitive Case) OU "casa"

--- Imprime das que têm o padräo ATÉ o final:

	sed -n '/Jose/,$p' contatos	--- , sign. até.

	sed -n '1,/Jose/p' contatos	--- Da 1a. linha até a palavra José


--- imprime tudo o que estiver ENTRE um padräo ATÉ outro:
	seq 100 | sed -n '/33/,/44/p' 	--- inclui os dois padröes (33 e 44)


--- Apaga determinada linha:

	sed '2d' contatos




ver tb:
http://www.theunixschool.com/2012/12/sed -10-examples-to-print-lines-from-file.html

