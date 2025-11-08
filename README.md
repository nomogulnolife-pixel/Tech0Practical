Step3-1　宿題パッケージstarterの課題対応後アプリです


##  TECH0 3-1 課題
　UI の実装は以下（Next.JS）
　frontend/"src/app"/customers/page.jsx
　処理ごとの関数定義　
　バックエンド呼び出し処理
  button クリックによる各処理の呼び出しの実装



 
  フロントエンドから呼び出された各処理が記述されている（FASTAPI)
　backend/app.py

/customers に対して

read =>
getリクエストでIDを返す

post
　create
  Jsonの内容をSQLにインサート

put
　UPDATE
　特定IDのデータを更新


delete
　特定IDのデータを削除


演習１　エラーID E0001

frontend/src/app/customers/fetchCustomers.js
    src/app/customers/fetchCustomers.js が未定義の状態
以下のパスに定義をする
frontend/.env
    NEXT_PUBLIC_API_ENDPOINT=http://localhost:8000 

演習２　エラーID E0002
src/app/customers/update/[id]/updateCustomer.js
　このなかのfetch処理でエラーを起こしている
　500 Internal Server Error

backend/db_control/crud.py
    update_customer　関数
        query = "お見事！E0002の原因はこのクエリの実装ミスです。正しく実装しましょう"　　処理の構文となっていない
    queryを明確に定義する
        query = update(mymodel).where(mymodel.customer_id == customer_id).values(values)

演習　エラーID E-0003 

frontend/src/app/customers/create/page.jsx
以下の状態ではNULLのままデータは更新可能
const handleSubmit = async (event) => {
        event.preventDefault();
        const formData = new FormData(formRef.current);

以下の処理を追加する　ただし警告までであり処理場はNULL登録可能
 // 1. formDataの中から"customer_id"を取り出し、変数に格納
        const customerId = formData.get("customer_id");
        
        // 2. もし、そのIDが空であったならば…
        if (!customerId) { 
            // アラートを表示
            alert("IDは必須です"); 
            // 処理を中断
            return; 
        }
さらに具体的にNULLを認めない処理を追加する
backend/db_control/mymodels.py

class Customers(Base):
    __tablename__ = 'customers'

  　NULLを不許可とする処理を追加（nullable=False）
    customer_id: Mapped[str] = mapped_column(primary_key=True, nullable=False)
