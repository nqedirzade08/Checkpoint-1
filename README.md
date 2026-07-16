# Checkpoint 1

LLM API (NVIDIA — DeepSeek modeli) istifadə edən kiçik tətbiq. Terminal üzərindən istifadəçi sual verir, model cavab qaytarır. API açarı `.env` faylı vasitəsilə environment variable kimi idarə olunur, request/response üçün xəta idarəetməsi tətbiq olunub.

## Qurulum

1. Virtual mühit yaradın:
   ```bash
   python -m venv venv
   source venv/bin/activate   # Windows: venv\Scripts\activate
   ```

2. Asılılıqları quraşdırın:
   ```bash
   pip install -r requirements.txt
   ```

3. `.env.example` faylını `.env` adı ilə kopyalayın:
   ```bash
   cp .env.example .env
   ```
   Sonra `.env` faylını açıb `NVIDIA_API_KEY` dəyərini öz API key-inizlə əvəz edin. Key-i [build.nvidia.com](https://build.nvidia.com) hesabınızdan əldə edə bilərsiniz.

   ⚠️ `.env` faylı `.gitignore` ilə istisna edilib — real key heç vaxt repository-yə düşmür. Yalnız `.env.example` (placeholder dəyərlə) repo-dadır.

4. Tətbiqi işə salın:
   ```bash
   python main.py
   ```

## Fayl strukturu

```
├── main.py           — əsas skript: API çağırışı, xəta idarəetməsi
├── .env.example       — API key konfiqurasiyası üçün nümunə (real key yoxdur)
├── .gitignore          — .env faylının commit olunmasının qarşısını alır
└── requirements.txt     — Python asılılıqları (openai, python-dotenv)
```

## Checkpoint 1 tələbləri necə qarşılanıb

- **API inteqrasiyası:** `main.py` içində `get_response()` funksiyası NVIDIA-nın OpenAI-uyğun endpoint-inə (`integrate.api.nvidia.com`) düzgün request göndərir və response-u emal edir.
- **Request/response idarəetməsi:** Boş mesaj yoxlanışı edilir, `try/except` bloku ilə bütün API xətaları (timeout, server xətası və s.) tutulur və istifadəçiyə aydın mesaj kimi göstərilir. `timeout` və `max_retries` parametrləri ilə etibarlılıq artırılıb.
- **API key environment variable-da:** Key `.env` faylından `python-dotenv` vasitəsilə oxunur, kodun içində heç yerdə açıq yazılmayıb.

## Nümunə sorğu/cavab log-ları

**Sorğu:** `Salam`
**Cavab:**
```
Wa alaikum assalam! How can I assist you today?
```

**Sorğu:** `5 + 5 neçə edir?`
**Cavab:**
```
5 + 5 = 10.
```

**Sorğu:** `Sən mükəmməlsən`
**Cavab:**
```
Çox sağ ol! Bu sözlər məni çox sevindirdi. 😊
Mən həmişə sənin üçün ən yaxşı şəkildə faydalı olmağa çalışıram. Sən də
mükəmməlsən! Hər hansı sualın və ya mövzuda yardıma ehtiyacın olsa, buradayam.
```


