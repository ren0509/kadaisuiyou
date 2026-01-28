sudo dnf update -y

sudo dnf install -y git　

sudo dnf install -y docker

sudo systemctl enable docker

sudo systemctl start docker

sudo mkdir -p /usr/local/lib/docker/cli-plugins/

sudo curl -SL https://github.com/docker/compose/releases/download/v2.36.0/docker-compose-linux-x86_64 -o /usr/local/lib/docker/cli-plugins/docker-compose

sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose

sudo usermod -aG docker ec2-user

再ログイン後に確認:


docker --version

docker compose version

gitからソースコードを取得

git clone https://github.com/ren0509/kadaisuiyou.git

cd kadaisuiyou

Docker コンテナのビルド・起動

docker compose up -d --build

正常に起動すると、以下のようなコンテナが起動する。

docker compose ps

mysql入力
 sudo docker compose exec mysql mysql example_db

 CREATE TABLE `access_logs` (
  `id` INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
  `user_agent` TEXT NOT NULL,
  `remote_ip` TEXT NOT NULL,
  `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE `bbs_entries` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
  `user_id` INT UNSIGNED NOT NULL,
  `body` TEXT NOT NULL,
  `image_filename` TEXT DEFAULT NULL,
  `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE `user_relationships` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
  `followee_user_id` INT UNSIGNED NOT NULL,
  `follower_user_id` INT UNSIGNED NOT NULL,
  `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE `users` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
  `name` TEXT NOT NULL,
  `email` TEXT NOT NULL,
  `password` TEXT NOT NULL,
  `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP
);

ALTER TABLE `users` ADD COLUMN icon_filename TEXT DEFAULT NULL;

ALTER TABLE `users` ADD COLUMN introduction TEXT DEFAULT NULL;

ALTER TABLE `users` ADD COLUMN cover_filename TEXT DEFAULT NULL;

ALTER TABLE `users` ADD COLUMN birthday DATE DEFAULT NULL;


 

