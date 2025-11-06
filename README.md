This is a FastAPI-Next.js repo

### git clone https://github.com/suzuyu33z/Practical_10.git

■ backend

- cd backend
- python3 -m venv backend_env (backend_env という名前の仮想環境を作成)
- ./backend_env/Script/activate.ps1 (powershell の場合)
- source backend_env/bin/activate (macOS/Linux の場合)
- pip install -r requirements.txt
- uvicorn app:app --reload

■ frontend

- cd frontend
- npm install
- npm run dev

■ http://localhost:3000/customers にアクセス


Tech0 課題　

frontend/src/app/create/page.jsx  UIを形作るソース

backend/db_control/crud.py  DBへの更新処理が走るソース

backend/db_control/CRM.db   実際のデータが格納されるDB

backend/db_control/mymodels.py データ処理内容が記載されている（null許可不許可）




