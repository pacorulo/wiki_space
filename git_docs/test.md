#!/bin/bash

#Usé el contador para hacer el proceso completo sólo en dos directorios y hacer las pruebas 
#antes de newnameizar el script y ejecutarlo pero sobre todo para evitar la primera entrada del
#fichero kk que era el . y entonces fallaría
contador=0
NUM_LINEA=1


#IFS marca qué es el salto de línea ya que sino al meter en la variable linea el contenido de cada dir
#habría resultado en error al meter en cada variable cada palabra al usar como separador el whitespace
#y no entender como una sola variable/línea cada nombre de fichero mp3 cuyo nombre vamos a cambiar
IFS=$'\n'

#Chequeamos que no hay parámetros pasados la script (aunque esto no es necesario pero viene de que éste 
#script era inicialmente copia de otro... que al newname no se parece en nada
if test $# -ne 1
then

	echo "El uso del shell es 'NOMBRE_DE_SHELL' 'DIR'"

	exit 1

else

	DIR=$1
	cd $DIR

	#Creamos el fichero temporal que contendrá los nombres de todos los dir de los discos
	touch kk

	#Se mete el contenido en el fichero, y sólo metemos nombres de directorios
	#y luego con el sed quitamos los espacios en blanco y ponemos un \ delante de cada
	#uno de ellos porque sino luego el ls no funcionaría (aunque eso pasaba antes del IFS
	#con lo que quizás no hacía falta al usar el IFS con salto de línea... who knows
	find . -type d 2> /dev/null > kk
	sed -i 's/ \+/\\ /g' kk

	#Leemos línea a línea el fichero kk con los nombres de los dir de los discos
	while read dir
	do
	
		#La primera línea de kk se evita porque era el .
		if [ $contador -eq 0 ]
		then
			contador=`expr $contador + 1`
		else

			echo "El directorio es: $dir"
			echo "Subdir.: " `ls -l "$dir" | egrep ^d | wc -l`

			#Si existen subdirectorios entonces la línea con el directorio padre se 
			#evita evaluar y así no hay errores
			if [ `ls -l "$dir" | egrep ^d | wc -l` -eq 0 ]
			then
				echo "entra"
				#oldname contiene los nombres originales
				#newname contiene los nombres newnamees
				#CANTANTE contiene el string a remover
				cd $dir
				ls . | grep \.flac > oldname

				LINEA=`head -1 oldname`
				CANTANTE=`echo $LINEA | cut -d"-" -f1|cut -d"." -f2`
				
				sed -e "s/.$CANTANTE/ /g" oldname > newname

				#Si oldname y listado tiene el mismo numero de lineas
				NUM_FLACS=`cat oldname | wc -l`
				NUM_FINAL=`cat newname | wc -l`
				#echo "NUM_FLACS=$NUM_FLACS"
				#echo "NUM_FINAL=$NUM_FINAL"

				if [[ "$NUM_FLACS" -eq "$NUM_FINAL" ]]
				then
					
					while [ "$NUM_LINEA" -le "$NUM_FINAL" ]
					do

						LINEA_FLACS=`head \-$NUM_LINEA ./oldname | tail -1`
						LINEA_FINAL=`head \-$NUM_LINEA ./newname | tail -1`
						#echo "LINEA_FLACS=$LINEA_FLACS"
						#echo "LINEA_FINAL=$LINEA_FINAL"
						
						echo "mv $LINEA_FLACS $LINEA_FINAL"
						mv $LINEA_FLACS $LINEA_FINAL

						NUM_LINEA=`expr $NUM_LINEA + 1`

					done

				fi


			fi

			NUM_LINEA=1
			rm oldname newname
			cd $DIR
			echo
			echo
			echo
			echo

		fi

	done < kk

fi

#Si llegamos aquí podemos newnameizar con éxito
exit 0

