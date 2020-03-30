Para poder realizar este pequeño proyecto hice los scripts de UFO-Nov-2014.tsv y UFO-Dic-2014.tsv. Estos dos scripts
los use con el comando curl( Raw link) y los junte en un solo script llamado UFOS-Nov-Dic-2014.tsv convirtiendo al momento
las tabulaciones a "|"

"curl"
curl -s --compressed https://raw.githubusercontent.com/hatshex/Command_Line/master/data/UFO-Nov-2014.tsv> UFO-Nov-2014.tsv
curl -s --compressed https://raw.githubusercontent.com/hatshex/Command_Line/master/data/UFO-Dic-2014.tsv> UFO-Dic-2014.tsv

"tr"
cat UFO-Nov-2014.tsv UFO-Dic-2014.tsv | tr ['\t'] ['|'] > "UFOS-Nov-Dic-2014.tsv"

"sort" y uniq"
cat UFOS-Nov-Dic-2014.tsv| uniq -c | sort -n -r


¿Cuántas observaciones totales?
Fueron 1025 observaciones, use el comando de wc "Word counter" (Elimine dos lineas que son los titulos de las columnas)

sed -i "1d" UFOS-Nov-Dic-2014.tsv
sed -i "1026d" UFOS-Nov-Dic-2014.tsv

cat UFOS-Nov-Dic-2014.tsv| wc -l


¿Cuál es el top 5 de estados?

Northumberland|PA
Apache Junction|AZ
Memphis|TN
San Diego|CA
Mumbai (India)|
cut -d'|' -f2-3 UFOS-Nov-Dic-2014.tsv|head -n5 

¿Cuál es el top 5 de estados por año?
Esta es la misma que la anterior pregunta ya que contamos estan ordenadas

¿Cuál es el mes con más avistamientos? ¿El día de la semana?
El mes con mas avistamientos es Noviembre con mas Observaciones
cat UFO-Nov-2014.tsv| wc -l
529
cat UFO-Dic-2014.tsv| wc -l
498
