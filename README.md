# Automatizaci-n-UI-con-WebDriverIO
Ejercicio de Automatización UI con WebDriver JavaScript
Automatización de UI con JavaScript y WebDriverIO
Este ejercicio tiene como objetivo enseñarte cómo automatizar pruebas de interfaz de usuario (UI) utilizando JavaScript y la biblioteca WebDriverIO.

Prerrequisitos
Conocimientos básicos de JavaScript
Conocimientos básicos de programación de pruebas automatizadas
Conocimientos básicos de Selenium WebDriver
Node.js y npm instalados en tu sistema
Configuración del entorno de desarrollo
Para comenzar, debemos crear un nuevo proyecto de Node.js y instalar WebDriverIO como dependencia de nuestro proyecto:

csharp
Copy code
npm init -y
npm install --save-dev webdriverio
Ejemplo de automatización de UI
A continuación, proporcionamos un ejemplo básico de código para automatizar la búsqueda en Google. Este ejemplo incluye la configuración básica de WebDriverIO y la escritura de una prueba que automatiza la búsqueda en Google.

javascript
Copy code
// archivo: test/specs/search.js
const assert = require('assert');

describe('Google Search', () => {
    it('should work', () => {
        browser.url('https://www.google.com');
        const searchInput = $('input[name="q"]');
        searchInput.setValue('WebDriverIO');
        browser.keys('Enter');
        const title = browser.getTitle();
        assert.strictEqual(title, 'WebDriverIO - Buscar con Google');
    });
});
Ejecución de la prueba
Para ejecutar la prueba, primero debemos especificar la configuración básica de WebDriverIO en un archivo wdio.conf.js:

yaml
Copy code
// archivo: wdio.conf.js
exports.config = {
    specs: [
        './test/specs/**/*.js'
    ],
    capabilities: [{
        browserName: 'chrome'
    }],
    logLevel: 'silent',
    coloredLogs: true,
    screenshotPath: './errorShots/',
    baseUrl: 'https://www.google.com',
    waitforTimeout: 10000,
    connectionRetryTimeout: 90000,
    connectionRetryCount: 3,
    framework: 'mocha',
    reporters: ['spec'],
    mochaOpts: {
        ui: 'bdd'
    }
};
Finalmente, ejecutamos la prueba con el siguiente comando:

Copy code
npx wdio wdio.conf.js
Si todo ha ido bien, deberías ver el resultado de la ejecución de la pr
