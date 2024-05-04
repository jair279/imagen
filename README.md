<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Enviar ubicación actual a través de WhatsApp</title>
<script>
// Función para obtener la ubicación y enviarla a través de WhatsApp
function enviarUbicacionWhatsApp() {
  // Verificar si el navegador soporta la geolocalización
  if (navigator.geolocation) {
    // Obtener la ubicación
    navigator.geolocation.getCurrentPosition(function(position) {
      // Obtener las coordenadas
      var latitud = position.coords.latitude;
      var longitud = position.coords.longitude;
      
      // Construir el enlace de Google Maps con las coordenadas
      var googleMapsUrl = "https://www.google.com/maps?q=" + latitud + "," + longitud;
      
      // Construir el enlace de WhatsApp con la ubicación de Google Maps
      var whatsappUrl = "https://wa.me/?text=" + encodeURIComponent(googleMapsUrl);
      
      // Abrir WhatsApp en una nueva pestaña con la ubicación de Google Maps
      window.open(whatsappUrl);
    }, function(error) {
      // Manejar errores de geolocalización
      alert("Error al obtener la ubicación: " + error.message);
    });
  } else {
    // Mostrar un mensaje de error si la geolocalización no es compatible
    alert("Lo siento, tu navegador no soporta la geolocalización.");
  }
}
</script>
</head>
<body>
<!-- Botón para obtener la ubicación y enviarla a través de WhatsApp -->
<button onclick="enviarUbicacionWhatsApp()">Enviar Ubicación a WhatsApp</button>
</body>
</html>
