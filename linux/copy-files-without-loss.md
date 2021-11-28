If we add a new disk and we want to copy files but avoiding any link duplication or bit loss we can use the method:

1. Go to the directory we want to copy
2. Then just execute:
	```
	(tar cvf - dir_a_copiar) | (cd /dir_padre_destino; tar xvf -)
	```
