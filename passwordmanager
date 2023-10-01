echo "Password Manager - Welcome!"

read -p "Service Name: " service_name
read -p "Username: " username
read -s -p "Password: " password
echo  

echo "$service_name:$username:$password" >> passwords.txt

echo "Thank you!"

password_file="passwords.txt"
echo "パスワードマネージャーへようこそ！"
while true; do
    echo "次の選択肢から入力してください(Add Password/Get Password/Exit):"
    read choice
    case "$choice" in
        "Add Password")
            read -p "サービス名を入力してください: " service_name
            read -p "ユーザー名を入力してください: " username
            read -s -p "パスワードを入力してください: " password
            echo  

            echo "$service_name:$username:$password" >> "$password_file"
            echo "パスワードの追加は成功しました。";;
        "Get Password")
            read -p "サービス名を入力してください: " query_service

            result=$(grep -i "^$query_service:" "$password_file")

            if [ -z "$result" ]; then
                echo "そのサービスは登録されていません。"
            else
                IFS=':' read -r -a fields <<< "$result"
                echo "サービス名: ${fields[0]}"
                echo "ユーザー名: ${fields[1]}"
                echo "パスワード: ${fields[2]}"
            fi;;
        "Exit")
            echo "Thank you!"
            break;;
        *)
            echo "入力が間違えています。Add Password/Get Password/Exit から入力してください。";;
    esac
done
