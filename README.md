# GPT3_Speech
GPT3 API ve TTS konuşmanızı sağlayacak kodları kullanabilirsiniz.

<b>PYTHON 3.6</b> Versiyonu kullanılmıştır. Bazı modüller desteklenmediği için bu versiyonu tercih ettim.

Bu kodları çalıştırabilmek için aşağıdaki modülleri yüklemeniz gerekir.

<code>pip install pyttsx3</code><br>
<code>pip install SpeechRecognition</code><br>
<code>pip install DateTime</code><br>
<code>pip install openai</code><br>
<code>pip install PyAudio==0.2.11</code><br>

Modülleri yükledikten sonra "YOUR-API" yazan kısıma kendi API kodunuzu eklemeniz gerekir.
Kendinize API anahtar almak için https://platform.openai.com/account/api-keys adresine gidip yeni bir API oluşturun.

Pyttsx3 modülünün türkçe dil desteği yok. Pyttsx3 aslında işletim sisteminiz Windows ise Kayıt Defterinde yer alan TTS'ler üzerinde çalışmaktadır. Kayıt defterinde bu kayıtlara;
\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Speech\Voices\Tokens
yolunu takip ederek ulaşabilirsiniz. Bende 3. sırada Türkçe TTS TTS_MS_TR-TR_TOLGA_11.0 bulunduğu için kodda <code>voices[2].id</code> şeklinde Microsoft Tolga seçilmiştir.
![alt text](https://blog.mustafaergul.net/wp-content/uploads/2023/03/Screenshot_2.png) <br>
Sizde eğer bu kısımda Microsoft Tolga yoksa eklemelisiniz.
