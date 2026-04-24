# Determine-el-DR-y-el-BDR
En esta actividad, examinará las funciones del DR y el BDR, y verá el cambio de las funciones cuando hay  un cambio en la red. Luego, modificará la prioridad para controlar las funciones y forzará una nueva elección.  Por último, verificará que los routers estén desempeñando la función deseada
Determinación del DR y el BDR en OSPFv2
Este repositorio contiene la documentación y el análisis técnico del laboratorio de OSPFv2 enfocado en la gestión de roles en redes multiacceso (Broadcast). 
El objetivo es comprender el proceso de elección de los routers DR (Designado) y BDR (Designado de Respaldo), y cómo manipular estos roles mediante prioridades.

🛠️ Desarrollo de la Actividad
Parte 1: El Proceso de Elección y ConvergenciaEn esta fase se analiza la jerarquía predeterminada basada en el Router ID y el comportamiento ante fallas:
Identificación inicial: Se utiliza show ip ospf neighbor para determinar los roles actuales. 
El router con el RID más alto (RC con 192.168.31.33) asume el rol de DR.
Monitoreo con Debug: Se activa debug ip ospf adj para visualizar las transiciones de estado en tiempo real durante los cambios topológicos.
Comportamiento No Apropiativo: Se comprueba que, al restaurar una interfaz caída, el router no reclama su rol original si ya hay un DR/BDR electo, garantizando la estabilidad de la red.

Parte 2: Modificación de Prioridad y Reelección ForzadaSe implementa una jerarquía personalizada modificando las prioridades de interfaz:
Configuración de Prioridades: Se asignan valores específicos (RA: 200, RB: 100, RC: 1) mediante el comando ip ospf priority.
Reinicio del Proceso: Para aplicar los cambios, se ejecuta clear ip ospf process en todos los routers. 
Esto derriba las adyacencias actuales y fuerza una votación inmediata basada en las nuevas prioridades.

💻 Comandos ClaveComando
Propósito Técnicoshow ip ospf neighborVerificar estados de adyacencia (FULL, 2-WAY) y roles.debug ip ospf adj
Analizar el intercambio de paquetes Hello y sincronización de LSDB.ip ospf priority <valor>Definir el peso de un router en la elección (0 = nunca es DR).clear ip ospf process
Forzar la actualización de la tabla de vecinos y reelección.

Laboratorio realizado para el estudio de topologías OSPF de área única en entornos Cisco CCNA.
