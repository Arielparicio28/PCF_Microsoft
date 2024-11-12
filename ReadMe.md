1. Crearé un nuevo proyecto de componente pasando los parámetros básicos mediante el comando `pac pcf init`.

2. `pac pcf init --namespace SampleNamespace --name LinearInputControl --template field --run-npm-install` es el 1er comando que ejecuto en mi terminal para inicializar un proyecto de Control de Framework de Componente de PowerApps (PCF, por sus siglas en inglés). El propósito principal de este comando es facilitar el desarrollo de un nuevo control personalizado para PowerApps.
   
   2.1. `pac pcf init`: Este es el comando base que indica a la CLI de Power Platform que inicialice un nuevo proyecto de PCF.
   
   2.2. `--namespace SampleNamespace`: Especifica el espacio de nombres para el control. Los espacios de nombres son una forma de agrupar y organizar el código para evitar conflictos de nombres.
   
   2.3. `--name LinearInputControl`: Define el nombre del nuevo control que se va a crear. En este caso, el nombre del control es "LinearInputControl".
   
   2.4. `--template field`: Indica que el nuevo control se basará en la plantilla "field". Las plantillas pueden ser diferentes tipos de controles (como field o dataset), que determinan la funcionalidad y estructura básica del control.
   
   2.5. `--run-npm-install`: Después de inicializar el proyecto, este flag ejecuta automáticamente el comando `npm install` para instalar todas las dependencias necesarias listadas en el archivo `package.json` del proyecto.

3. El archivo `ControlManifest.Input.xml` es: El manifiesto de control es un archivo XML que contiene los metadatos del componente de código. También define el comportamiento del componente de código. 

   3.1. `namespace` Espacio de nombres del componente de código.

   3.2. `constructor` Constructor del componente de código.

   3.3. `version` Versión del componente. Cada vez que actualice el componente, deberá actualizar la versión para ver los cambios más recientes en el tiempo de ejecución.

   3.4. `display-name-key` Nombre del componente de código que se muestra en la interfaz de usuario.

   3.5. `description-key` Descripción del componente de código que se muestra en la interfaz de usuario.

   3.6. `control-type` Tipo de componente de código. Esto será un control.standard


4. insertare un elemento `type-group` Este elemento especifica el valor del componente y puede contener valores enteros, monetarios, de punto flotante o decimales.numberscontrol  

5. Ahora editare el elemento de propiedad (property)
Antes: `<property name="sampleProperty" display-name-key="Property_Display_Key" description-key="Property_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />`

Cambiado a: `<property name="controlValue" display-name-key="Control Value" description-key="Control value description" of-type-group="numbers" usage="bound" required="true" />`

6. Ahora editar el elemento recursos (resources)

Antes: `<resources> <code path="index.ts" order="1"/> <resources/>`

Cambiado a: `<resources> <code path="index.ts" order="1"/> <css path="css/LinearInputControl.css" order="1" />  <resources/>`

Así agregue el elemento css.

7. Generar el archivo `ManifestTypes.d.ts` con el siguiente comando. `npm run refreshTypes`


8. Implementación de la lógica " El siguiente paso después de implementar el archivo de manifiesto es implementar la lógica del componente mediante TypeScript." la lógica se implementa en el archivo `index.ts`

9. Definí variables privadas en el archivo `index.ts`, estas variables privadas permiten a la clase LinearInputControl manejar su estado interno, interactuar con el DOM para mostrar y capturar datos del usuario, y comunicarse con el framework de PowerApps para integrarse correctamente en una aplicación de PowerApps.
