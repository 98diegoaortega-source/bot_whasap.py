# bot_whasap.py
from flask import Flask, request
from twilio.twiml.messaging_response import MessagingResponse

app = Flask(__name__)

@app.route("/bot", methods=['POST'])
def bot():
    mensaje = request.form.get('Body')  # Mensaje recibido
    respuesta = MessagingResponse()

    if mensaje.lower() == "hola":
        respuesta.message("Hola! Bienvenido a Diego Tech Solutions.")
    else:
        respuesta.message(f"Recibí tu mensaje: {mensaje}")

    return str(respuesta)

if __name__ == "__main__":
    app.run(debug=True)
