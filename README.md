# DEU Web Kayit Notifier 📢

Bu Python botu, **Dokuz Eylül Üniversitesi (DEU) ders kayıt sistemini** takip ederek açılan dersleri otomatik olarak tespit eder ve WhatsApp ile bildirim gönderir.

## 🚀 Özellikler

- Üniversitenin ders kayıt sayfasına otomatik giriş yapar.
- Sadece belirlenen dersleri takip eder.
- Ders kontenjanı açıldığında WhatsApp üzerinden bildirim yollar.
- Sürekli çalışarak her 1 dakikada bir kontrol eder.

---

## 📦 Kurulum

Bu botu çalıştırmak için aşağıdaki adımları izleyin.

### **1️⃣ Gerekli Bağımlılıkları Yükleyin**

Python bağımlılıklarını yüklemek için:

```bash
pip3 install -r requirements.txt
```

Eğer `requirements.txt` dosyanız yoksa, aşağıdaki komutla bağımlılıkları yükleyebilirsiniz:

```bash
pip3 install selenium python-dotenv twilio
```

### **2️⃣ Chrome ve ChromeDriver Yükleyin**

Bu bot, **Selenium** kullanarak web sayfalarını otomatik olarak kontrol eder. Bunun için **Google Chrome** ve **ChromeDriver** yüklemelisiniz.

#### **🔹 Chrome Yükleme**

Eğer sisteminizde Chrome yüklü değilse aşağıdaki bağlantıdan indir:

- [Google Chrome İndir](https://www.google.com/chrome/)

#### **🔹 ChromeDriver Yükleme**

1. Google Chrome sürümünü kontrol edin:
   ```bash
   google-chrome --version   # Linux
   google-chrome-stable --version  # Linux bazı dağıtımlar
   chromedriver --version  # Mac ve Windows
   ```
2. Chrome'un sürümüne uygun **ChromeDriver'ı** şu bağlantıdan indir:
   - [ChromeDriver İndir](https://sites.google.com/chromium.org/driver/)
3. İndirilen `chromedriver` dosyasını `/usr/local/bin/` veya **projenin kök dizini** içine taşıyın:
   ```bash
   sudo mv chromedriver /usr/local/bin/
   sudo chmod +x /usr/local/bin/chromedriver
   ```

---

### **3️⃣ Twilio Hesabı Açın ve WhatsApp API'sini Kullanın**

Bu bot, WhatsApp üzerinden bildirim gönderecektir. Bunun için **Twilio API** kullanılır.

#### **🔹 Twilio Hesabı Açma**

1. [Twilio](https://www.twilio.com/) web sitesine giderek bir hesap oluşturun.
2. Ücretsiz deneme kredisi ile başlayabilirsiniz.
3. **WhatsApp API erişimi** için Twilio'nun [WhatsApp Business API](https://www.twilio.com/whatsapp) sayfasına gidin.
4. Hesabınızı doğruladıktan sonra **Account SID**, **Auth Token** ve **Twilio WhatsApp numaranızı** edinin.

#### **🔹 WhatsApp Numarasını Bağlama**

1. Twilio panelinden **Send a WhatsApp Message** seçeneğini açın.
2. Kendi numaranızı ekleyin ve onaylayın.
3. Twilio'dan gelen mesajı onayladıktan sonra API'yı kullanabilirsiniz.

---

### **4️⃣ .env Dosyasını Hazırlayın**

**Gizli bilgileri saklamak için** `.env` dosyası oluşturun ve aşağıdaki bilgileri ekleyin:

```ini
DEU_USERNAME=ogrenci_kullanici_adi
DEU_PASSWORD=ogrenci_sifresi
TWILIO_ACCOUNT_SID=twilio_account_sid
TWILIO_AUTH_TOKEN=twilio_auth_token
TWILIO_WHATSAPP_NUMBER=whatsapp_sending_number
MY_WHATSAPP_NUMBER=your_whatsapp_number
```

`.env` dosyasını **GitHub'a yüklemeyin!** `.gitignore` içine şu satırı ekleyin:

```
.env
```

---

## 🏃‍♂️ Çalıştırma

Takip etmek istediğiniz dersleri `TARGET_COURSES` listesine ekleyin:

```python
TARGET_COURSES = [
    "BİL 3112 Makine Öğrenimi",
    "BİL 4108 Fizik",
    "BİL 4112 Yapay Zeka",
]
```

Botu çalıştırmak için şu komutu kullanın:

```bash
python3 deu-ders-kayit-bot.py
```

Bot her 1 dakikada bir çalışarak **ders kontenjanlarını kontrol eder** ve **yeni açılan dersleri WhatsApp üzerinden bildirir**.
Eğer bir önceki ve bir sonraki bildirim aynı olacaksa bildirim göndermez, sadece yeni eklenen dersleri bildirir.

---

## 📜 Katkıda Bulunma

Bu projeye katkıda bulunmak isterseniz:

1. Reponun bir kopyasını alın (Fork yapın).
2. Yeni bir özellik ekleyerek veya hata düzelterek PR (Pull Request) açın.
3. Sorularınız varsa **GitHub Issues** kısmında belirtebilirsiniz.

---

## 📜 Lisans

Bu proje **MIT Lisansı** altında yayınlanmıştır. Özgürce kullanabilir, değiştirebilir ve geliştirebilirsiniz!

---

🔹 **Proje Sahibi:** gokalpcayci
🔹 **Repo:** https://github.com/gokalpcayci
