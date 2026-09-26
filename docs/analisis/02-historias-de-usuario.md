# Historias de Usuario

## Aplicación móvil de gestión comercial de mayoristas de papa

Las historias de usuario priorizadas describen las necesidades principales de los actores del sistema y orientan el alcance funcional del producto mínimo viable.

| ID | RF relacionados | Historia de usuario | Criterio principal de aceptación |
|---|---|---|---|
| HU01 | RF05, RF06, RF06A, RF06B | Como mayorista o encargado que lo reemplaza, quiero registrar al proveedor, las variedades y el peso de cada saco durante la descarga. | El sistema agrupa los pesos por variedad, acumula totales parciales y generales, y permite cerrar el cargamento. |
| HU02 | RF07, RF14 | Como encargado, quiero registrar el precio acordado, el flete, los adelantos y la forma de pago para calcular el monto líquido del proveedor. | El sistema resta flete y adelantos, registra pago al contado o en cuotas, y mantiene el saldo pendiente. |
| HU03 | RF08, RF10, RF13, RF15 | Como encargado, quiero registrar un despacho mayorista a otro departamento con sacos, variedades y flete acordados. | La venta identifica comprador, destino, vehículo y cantidades, y flete; descuenta existencias y genera cobro o saldo. |
| HU04 | RF13, RF14, RF15 | Como mayorista, quiero consultar obligaciones y cobranzas por vencimiento para priorizar pagos y seguimiento. | La consulta muestra origen, vencimiento, abonos y saldo actualizado. |
| HU05 | RF04, RF08, RF17 | Como mayorista, quiero revisar existencias por variedad y lote para decidir qué mercadería vender o reponer. | El tablero muestra saldo, antigüedad y movimientos trazables. |
| HU06 | RF21, RF22 | Como encargado que reemplaza al mayorista, quiero pesar e ingresar compras y ventas cuando se interrumpa Internet. | La operación autorizada queda pendiente y se sincroniza una sola vez al recuperar conexión. |
| HU07 | RF19, RF17 | Como mayorista, quiero que la IA analice la información acumulada para descubrir tendencias y patrones y, cuando sea posible, estimar el precio semanal. | El tablero diferencia resultados descriptivos de predicciones, e indica periodo, rango, confianza y comparación con el valor real. |