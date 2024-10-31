# Transcritor-de-Audio
Aplicativo transcritor de áudio que utiliza a biblioteca streamlit e a biblioteca assemblyai do Python
import assemblyai as aai
import streamlit as st

st.markdown("""
    <style>

    .stApp {
        background-color: #ffb6c1;
    }

    .header {
        text-align: center;
        color: white;
        border-radius: 15px;
    }
    
    .transcription {
        font-family: Arial, sans-serif;
        color: #333;
        background-color: #f4f4f4;
        padding: 20px;
        border-radius: 5px;
        margin-top: 20px;
    }
    </style>
    
""", unsafe_allow_html=True)


st.markdown("<h1 class='header'>Transcritor de Áudio</h1>", unsafe_allow_html=True)
st.markdown("<h2>Transcreva o áudio que você quiser!</h2>", unsafe_allow_html=True)


url = st.text_input('Digite o URL:')
upload = st.file_uploader("Escolha um arquivo:", type='mp4')


aai.settings.api_key = "bcbb2a631d564a80a9cc16f8fe371ac4"
transcriber = aai.Transcriber()

if upload is not None:
    transcript = transcriber.transcribe(upload)
    
    st.markdown("<div class='transcription'>Essa é a transcrição do áudio que você fez upload:</div>", unsafe_allow_html=True)
    st.write(transcript.text)

