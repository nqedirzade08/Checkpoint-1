# LLM Əsaslı Tətbiq — Checkpoint 1

## Qurulum

1. Virtual mühit yaradın (istəyə bağlı, tövsiyə olunur):
   ```bash
   python -m venv venv
   source venv/bin/activate   # Windows: venv\Scripts\activate
   ```

2. Asılılıqları quraşdırın:
   ```bash
   pip install -r requirements.txt
   ```

3. `.env.example` faylını `.env` adı ilə kopyalayın və öz API key-inizi daxil edin:
   ```bash
   cp .env.example .env
   ```
   Sonra `.env` faylını açıb `NVIDIA_API_KEY` dəyərini real key-inizlə əvəz edin.

   ⚠️ **VACIB:** Daha əvvəl paylaşdığınız key artıq ifşa olunub sayılır —
   provayderin panelindən onu ləğv edib (revoke) yeni key yaradın.

4. Tətbiqi işə salın:
   ```bash
   python main.py
   ```

## Struktur

- `main.py` — əsas skript, LLM API-yə sorğu göndərir və cavabı emal edir
- `.env.example` — nümunə environment variable faylı (real key saxlamır)
- `.gitignore` — `.env` faylının GitHub-a düşməsinin qarşısını alır
- `requirements.txt` — layihə üçün lazım olan Python paketləri

## Checkpoint 1 tələbləri necə qarşılanıb

- **API inteqrasiyası**: `main.py` içində `get_response()` funksiyası düzgün
  request göndərir və response-u emal edir.
- **Request/response idarəetməsi**: try/except bloku ilə xətalar tutulur,
  boş mesaj yoxlanışı edilir.
- **API key environment variable-da**: key `.env` faylından `python-dotenv`
  vasitəsilə oxunur, kodun içində heç yerdə açıq yazılmayıb.
