---
description: La siguiente información le ayuda a realizar una campaña de adquisición de elementos heredados de ida y vuelta basada en la huella de un dispositivo mediante un vínculo de marketing.
seo-description: La siguiente información le ayuda a realizar una campaña de adquisición de elementos heredados de ida y vuelta basada en la huella de un dispositivo mediante un vínculo de marketing.
seo-title: Prueba de adquisición de elementos heredados
solution: Experience Cloud,Analytics
title: Prueba de adquisición de elementos heredados
uuid: e0591f4a-e26b-4fe4-97c1-a6831a926fa5
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '272'
ht-degree: 100%

---


# Prueba de adquisición de elementos heredados {#testing-legacy-acquisition}

La siguiente información le ayuda a realizar una campaña de adquisición de elementos heredados de ida y vuelta basada en la huella de un dispositivo mediante un vínculo de marketing.

Si la aplicación móvil aún no está en Google Play, puede seleccionar cualquier aplicación móvil como destino al crear el vínculo de campaña. Esto solo determina a qué aplicación lo redirige el servidor de adquisición después de hacer clic en el vínculo de adquisición, y no afecta a la capacidad para probar el vínculo.

1. Vaya a **[!UICONTROL Uso de vínculos de adquisición de elementos heredados]** en Adobe Mobile Services y genere una URL de campaña de adquisición.

   Para obtener más información, consulte [Uso de vínculos de adquisición de elementos heredados](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).

1. En el dispositivo móvil en el que va a instalar la aplicación, haga clic en el vínculo generado.

   Los servidores de Adobe (`c00.adobe.com`) almacenan la huella digital y después redirigen al App Store. No es necesario descargar la aplicación para realizar pruebas.

1. En el mismo dispositivo móvil utilizado en el paso 2, inicie la aplicación por primera vez.

   La forma más sencilla de asegurarse de que esto suceda es eliminar e instalar la aplicación de nuevo.

Recuerde la información siguiente:

* El servidor de adquisición proporciona una coincidencia de atribución basada en la dirección IP y en la información de usuario-agente que se registra al hacer clic en vínculo (paso 2) y al iniciarse la aplicación (paso 3).
* Mediante herramientas de monitoreado HTTP, las visitas enviadas desde la aplicación pueden monitorizarse para verificar la atribución de adquisición.

>[!TIP]
>
>Cualquier variación en el usuario-agente enviado puede provocar el fallo de la atribución.
