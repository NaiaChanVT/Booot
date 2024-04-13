// Proyecto 95rk16
// (c) SniaStudios. Todos sus derechos reservados.
// Cualquier copia del archivo que sea robado, se procedera legalmente. Evite la reimpresion de este.
// Bot en fase [Beta] con la ultima actualizacion: 0.1.5_Beta

const tmi = require('tmi.js')
 const axios = require('axios');
 const OpenAI = require('openai-node');
 const fetch = require('node-fetch');

const options = {
    options: {
        debug: true
    },
    connection: {
        reconnect: true
    },
    identity: {
        username: '95rk16',
        password:'oauth:v5kvni3ui028ymr8vzeo5td3i5a834'
    },
    channels: ['fijev68799'] // ['wdatsu', '95rk16']
}

const client = new tmi.client(options)


client.connect();





// 🌸ꗥ～ꗥ🌸 𝐈𝐍𝐈𝐂𝐈𝐎 𝐃𝐄 𝐋𝐀 𝐒𝐄𝐂𝐂𝐈𝐎𝐍 𝐃𝐄 𝐌𝐎𝐃𝐄𝐑𝐀𝐂𝐈𝐎𝐍 🌸ꗥ～ꗥ🌸

client.on('message', (target, ctx, message, self) => {
  if (self) return;

  // Eliminar los caracteres no alfabéticos del mensaje
  const cleanedMessage = message.replace(/[^a-zA-Z]/g, '');

  // Verificar si el mensaje limpio está completamente en mayúsculas
  if (cleanedMessage === cleanedMessage.toUpperCase() && cleanedMessage.length > 0) {
      // Enviar mensaje de advertencia al usuario
      client.say(target, `@${ctx.username} Demasiadas mayúsculas en este mensaje [warning]`);
  }
});

// 🌸ꗥ～ꗥ🌸 𝐅𝐈𝐍𝐀𝐋 𝐃𝐄 𝐋𝐀 𝐒𝐄𝐂𝐂𝐈𝐎𝐍 𝐃𝐄 𝐌𝐎𝐃𝐄𝐑𝐀𝐂𝐈𝐎𝐍 🌸ꗥ～ꗥ🌸





// 🌸ꗥ～ꗥ🌸 𝐈𝐍𝐈𝐂𝐈𝐎 𝐃𝐄 𝐋𝐀 𝐒𝐄𝐂𝐂𝐈𝐎𝐍 𝐃𝐄 𝐎𝐏𝐂𝐈𝐎𝐍𝐄𝐒 𝐀𝐕𝐀𝐍𝐙𝐀𝐃𝐀𝐒 🌸ꗥ～ꗥ🌸

function sendMessage(message) {
  client.say('#fijev68799', message);
}

// Preguntas y respuestas predefinidas
const conversation = {
  "hola": "¡Hola! ¿Cómo estás?",
  "eres un bot?": "No preguntes estupideses",
  "cómo estás?": "Estoy bien, ¡gracias por preguntar!",
  "quiero mod": "Recuerda no pedir o seran timeados o baneados",
  "quiero vip": "Recuerda no pedir o seran timeados o baneados",
  "cuál es tu comida favorita?": "Soy un bot, así que no como. Pero me gusta la programación.",
  "adiós": "¡Hasta luego! Que tengas un buen día."
};

// Evento para manejar los mensajes del chat
client.on('chat', (target, ctx, message, self) => {
  if (self) return;

  // Convertir el mensaje a minúsculas para evitar problemas de mayúsculas y minúsculas
  const lowercaseMessage = message.toLowerCase();

  // Verificar si el mensaje coincide con alguna pregunta en la conversación
  if (conversation[lowercaseMessage]) {
      sendMessage(conversation[lowercaseMessage]);
  }
});

// 🌸ꗥ～ꗥ🌸 𝐅𝐈𝐍𝐀𝐋 𝐃𝐄 𝐋𝐀 𝐒𝐄𝐂𝐂𝐈𝐎𝐍 𝐃𝐄 𝐎𝐏𝐂𝐈𝐎𝐍𝐄𝐒 𝐀𝐕𝐀𝐍𝐙𝐀𝐃𝐀𝐒 🌸ꗥ～ꗥ🌸





// 🌸ꗥ～ꗥ🌸 𝐈𝐍𝐈𝐂𝐈𝐎 𝐃𝐄 𝐋𝐀 𝐒𝐄𝐂𝐂𝐈𝐎𝐍 𝐃𝐈𝐕𝐄𝐑𝐒𝐈𝐎𝐍 / 𝐈𝐍𝐓𝐄𝐑𝐀𝐂𝐂𝐈𝐎𝐍 🌸ꗥ～ꗥ🌸

// Lista de palabras aleatorias para @95rk16
const responses95rk16 = [
  "la más pro",
  "la más pendeja",
  "La mejor mod MODS",
  "¿Qué quieres, wei?",
  "nmms, soy un bot"
];

// Lista de palabras aleatorias para @nightbot
const responsesNightbot = [
  "Ahhh...? Hay otros bots aqui? Genial...",
  "La vida apesta, y mas si estas aqui nightbot",
  "Francamente ser tú ya es burla suficiente",
  "Un bot mas que soportar...",
  "Eres lo peor.",
  "UGH, Bots...",
  "¡UGH! Espacio personal, gente!",
  "No me hables.",
  "Oh, no ¿eres tu? Sabes donde esta el buzón de quejas? Madge",
  "Hagamoslo facil, yo esperare aqui y tú ve y modera",
  "A quien le importas?"
];

// Índices de respuesta anteriores para evitar repeticiones
let lastResponseIndex95rk16 = -1;
let lastResponseIndexNightbot = -1;

client.on('chat', (target, ctx, message, self) => {
  if (self) return;

  // Normaliza el mensaje a minúsculas para manejar diferentes variantes
  const normalizedMessage = message.trim().toLowerCase();

  // Verifica si el mensaje menciona a @95rk16 o 95rk16
  if (normalizedMessage.includes('@95rk16') || normalizedMessage.includes('95rk16')) {
    let responseIndex = Math.floor(Math.random() * responses95rk16.length);

    // Asegúrate de que no se repita la misma respuesta dos veces seguidas
    while (responseIndex === lastResponseIndex95rk16) {
      responseIndex = Math.floor(Math.random() * responses95rk16.length);
    }

    lastResponseIndex95rk16 = responseIndex;

    // Envía la respuesta aleatoria para 95rk16
    const randomResponse = responses95rk16[responseIndex];
    client.say(target, `${randomResponse}`);
  }

  // Verifica si el mensaje menciona a @nightbot o nightbot
  if (normalizedMessage.includes('@nightbot') || normalizedMessage.includes('nightbot')) {
    let responseIndex = Math.floor(Math.random() * responsesNightbot.length);

    // Asegúrate de que no se repita la misma respuesta dos veces seguidas
    while (responseIndex === lastResponseIndexNightbot) {
      responseIndex = Math.floor(Math.random() * responsesNightbot.length);
    }

    lastResponseIndexNightbot = responseIndex;

    // Envía la respuesta aleatoria para nightbot
    const randomResponse = responsesNightbot[responseIndex];
    client.say(target, `${randomResponse}`);
  }
});


// Función para obtener un chiste aleatorio en español desde la API de Chistes Random
async function getSpanishJoke() {
  try {
      const response = await axios.get('https://api.chucknorris.io/jokes/random');
      return response.data.value;
  } catch (error) {
      console.error('Error al obtener el chiste en español:', error.message);
      return 'No pude encontrar un chiste en español en este momento, lo siento.';
  }
}

// Comando para solicitar un chiste en español
client.on('chat', async (target, ctx, message, self) => {
  if (self) return;

  const commandName = message.trim();

  if (commandName === "!chiste") {
      const joke = await getSpanishJoke();
      client.say(target, joke);
  }
});

// 🌸ꗥ～ꗥ🌸 𝐅𝐈𝐍𝐀𝐋 𝐃𝐄 𝐋𝐀 𝐒𝐄𝐂𝐂𝐈𝐎𝐍 𝐃𝐈𝐕𝐄𝐑𝐒𝐈𝐎𝐍 / 𝐈𝐍𝐓𝐄𝐑𝐀𝐂𝐂𝐈𝐎𝐍 🌸ꗥ～ꗥ🌸





// 🌸ꗥ～ꗥ🌸 𝐈𝐍𝐈𝐂𝐈𝐎 𝐃𝐄 𝐋𝐀 𝐒𝐄𝐂𝐂𝐈𝐎𝐍 𝐃𝐄 𝐂𝐎𝐌𝐀𝐍𝐃𝐎𝐒 🌸ꗥ～ꗥ🌸

// Objeto para realizar el seguimiento de los tiempos de cooldown
const cooldowns = {};

// Evento de chat para manejar los mensajes
client.on('message', async (channel, ctx, message, self) => {
    // Ignorar mensajes del propio bot
    if (self) return;

    // Verificar si el mensaje es el comando !followage
    const commandName = message.trim().toLowerCase();
    if (commandName === '!followage') {
        const userId = ctx.username;

        // Verificar si el usuario tiene un cooldown activo
        if (cooldowns[userId] && Date.now() < cooldowns[userId]) {
            // Si el usuario está en cooldown, no ejecutar el comando y notificarle
            client.say(channel, `@${ctx.username}, debes esperar un poco antes de usar este comando nuevamente.`);
            return;
        }

        try {
            // Construir la URL con los parámetros del canal y usuario
            const url = `https://decapi.me/twitch/followage/${channel.slice(1)}/${ctx.username}?token=ua2iK85ukL30jI6DExyNIkAYer8nlDGXo7nJFaws`;

            // Realizar la solicitud HTTP a la URL especificada
            const response = await axios.get(url);

            // Responder en el chat con la respuesta de la solicitud
            client.say(channel, `@${ctx.username} ${response.data}`);

            // Establecer el cooldown de 30 segundos para este usuario
            cooldowns[userId] = Date.now() + 30000; // 30 segundos en milisegundos
        } catch (error) {
            console.error('Error al obtener el followage:', error);
            client.say(channel, `Hubo un problema al obtener el followage.`);
        }
    }
});

// Función para obtener el estado del clima
async function getWeather(city) {
  try {
      const apiKey = 'aff3799e65c05d10f42ca23fec374b75'; // Reemplaza 'tu_api_key' con tu propia clave de API de OpenWeatherMap
      const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;
      const response = await axios.get(apiUrl);
      const weatherData = response.data;
      const weatherDescription = weatherData.weather[0].description;
      const temperature = weatherData.main.temp;
      const cityName = weatherData.name;
      return `El clima en ${cityName} es ${weatherDescription} con una temperatura de ${temperature}°C.`;
  } catch (error) {
      console.error('Error al obtener el estado del clima:', error.response.data.message);
      return 'Lo siento, no pude obtener el estado del clima en esta ubicación.';
  }
}

// Evento para manejar los mensajes del chat
client.on('message', async (channel, tags, message, self) => {
  if (self) return;

  // Verificar si el mensaje es el comando "!clima"
  if (message.startsWith('!clima')) {
      // Obtener el nombre de la ciudad del mensaje (el comando debe ser "!clima ciudad")
      const city = message.split(' ')[1];
      if (!city) {
          client.say(channel, 'Por favor, proporciona el nombre de una ciudad después del comando.');
          return;
      }

      // Obtener el estado del clima para la ciudad especificada
      const weather = await getWeather(city);
      // Enviar el estado del clima al chat
      client.say(channel, weather);
  }
});

// Lista de comandos y respuestas
const commands = {
  '!redes': () => `/me 📷 I N S T A G R A M 📷  https://www.instagram.com/????? 🐦 T W I T T E R 🐦  https://twitter.com/95rk16 VoHiYo S U P P O R T VoHiYo https://twitter.com/95rk16Support`,
  '!vip': () => `Hola :D para tener VIP en el canal debes ver al menos 15 hrs y comentar para ganártelo uwu usa !watchtime para saber cuántas horas llevas OuO`,
  '!sniping': () => `SI HACES STREAM SNIPING Y SE DESCUBRE, SERÁS BANEADO PERMANENTE, SEAS MOD, SUB O VIP PeepoAnalise`,
  '!ts': () => `$(urlfetch https://2g.be/twitch/following.php?user=$(touser)&channel=$(channel)&format=mwdhms)`,
  '!9bianb': (ctx) => `私はこのユーザーによって作成された人工知能です。私はベータ段階にあります。私はこのチャンネルのヘルプ ロボットです。他に質問しないでください。OK? ${ctx.username}`,
  'KEKW': () => `KEKW KEKW`,
  '!reglas': () => `1-NO pedir MOD,SUB,VIP 🍥 2-NO usar el /me 🍥 3-NO Hacer SPAM 🍥 4-NO DONACIONES FALSAS 🍥 5-NO LINKS 🍥 6-NO SER TOXICO LS 🍥 7-NO usar idiomas no entendibles como chino, ruso, etc. 🍥 8-No pedir que juegue algo o con alguien 🍥 wdtsBAN`,
  '😎': () => `Qué? ¿Te crees muy vrgas? GlitchCat`,
  'RainbowPls': () => `RainbowPls RainbowPls`,
  '¡uptime': (ctx) => `!uptime ${ctx.username}`
};

// Manejador de eventos de chat
client.on('message', (channel, ctx, message, self) => {
  // Ignora los mensajes del bot
  if (self) return;

  // Limpia y divide el mensaje para obtener el comando
  const commandName = message.trim().split(' ')[0];

  // Verifica si el comando existe en la lista de comandos
  if (commands.hasOwnProperty(commandName)) {
      try {
          // Ejecuta el comando y envía la respuesta al chat
          const response = commands[commandName](ctx);
          if (response) {
              client.say(channel, response);
          }
      } catch (error) {
          console.error('Error al ejecutar el comando:', error);
      }
  }
});

// 🌸ꗥ～ꗥ🌸 𝐅𝐈𝐍𝐀𝐋 𝐃𝐄 𝐋𝐀 𝐒𝐄𝐂𝐂𝐈𝐎𝐍 𝐃𝐄 𝐂𝐎𝐌𝐀𝐍𝐃𝐎𝐒 🌸ꗥ～ꗥ🌸





// 🌸ꗥ～ꗥ🌸 𝐈𝐍𝐈𝐂𝐈𝐎 𝐃𝐄 𝐋𝐀 𝐒𝐄𝐂𝐂𝐈𝐎𝐍 𝐃𝐄 𝐓𝐄𝐌𝐏𝐎𝐑𝐈𝐙𝐀𝐃𝐎𝐑𝐄𝐒 🌸ꗥ～ꗥ🌸 

// Función para enviar un mensaje específico al chat
function sendMessage(message) {
    client.say('#fijev68799', message);
}

// Temporizador 1: Mensaje cada 1 minuto
setInterval(() => {
    sendMessage('🌟🌟 TWITTER 🌟🌟 https://twitter.com/95rk16');
}, 600000);

// Temporizador 2: Mensaje cada 1.5 minutos
setInterval(() => {
    sendMessage('Recuerda que puedes suscribirte GRATIS usando Amazon Prime, entra al link para activar tu primer mes Totalmente GRATIS y disfruta de los beneficios!! https://gaming.amazon.com/ wdtsHYPERS wdtsHYPERS');
}, 9000000);

// Puedes añadir más temporizadores aquí...

// Temporizador N: Mensaje cada cierto intervalo
// setInterval(() => {
//     sendMessage('Mensaje cada cierto intervalo');
// }, intervalo_en_milisegundos);

// 🌸ꗥ～ꗥ🌸 𝐅𝐈𝐍𝐀𝐋 𝐃𝐄 𝐋𝐀 𝐒𝐄𝐂𝐂𝐈𝐎𝐍 𝐃𝐄 𝐓𝐄𝐌𝐏𝐎𝐑𝐈𝐙𝐀𝐃𝐎𝐑𝐄𝐒 🌸ꗥ～ꗥ🌸