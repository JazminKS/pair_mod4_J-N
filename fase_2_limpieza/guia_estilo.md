MOVIMIENTOS
1. Mover columna 'employeenumber' al principio y hacerla PK para identificar a los empleados (o dejarla en ese sitio como PK)
2. Eliminar Unnamed:0

Cambio DType
1. age > int
2. ¿Qué son los object? Cambiarlos si no proceden
3. gender > string
4. datebirth > date

Ortotipografia
1. Definir columnas a renombrar:
2. Cambiar todo a minúsculas, definir en qué columnas: ANA

Otros
1. remotework > unificar a yes/no (ahora está yes/no, true/false, 1/0)
2. gender > unificar de 0/1 a male/female
3. Cambiar nan por none: marital status, businesstravel, department, educationfield, hourlyrate, monthlyincome,
						over18, overtime, standardhours, yearsincurrentrole, roledepartament, numberchildren, salary  ANA
4. Ponerle dos decimales al dailyrate ANA
5. Poner el significado de cada numero en education?