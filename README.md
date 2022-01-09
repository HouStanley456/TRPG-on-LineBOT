Ubuntu 18.04
--Python game with linebot--

1.On CMD:

step 1:
    sudo apt-get update ;
    sudo apt-get install -y python3-pip unzip ;
    sudo timedatectl set-timezone Asia/Taipei ;
    pip3 install flask line-bot-sdk uwsgi ;
    source .profile 

step 2:
    sudo apt-get update ;
    sudo apt-get install -y nginx ;
    sudo timedatectl set-timezone Asia/Taipei; 
    sudo snap install core ;
    sudo snap refresh core ;
    sudo snap install --classic certbot ;
    sudo ln -s /snap/bin/certbot /usr/bin/certbot

step 3:
    sudo ln -s /etc/nginx/sites-available/line.conf /etc/nginx/sites-enabled/line.conf
    sudo vim /etc/nginx/sites-available/line.conf

    paste on line.conf
    '''

    server {
        server_name YOUR_SERVER_NAME;

        # for LINE Bot
        location / {
            include uwsgi_params;
            #uwsgi_pass unix:/home/your_account/your_project_name/your_project_name.sock;
            uwsgi_pass 127.0.0.1:3000;
            #proxy_pass https://your_url;
        }
        # for Web or LIFF
        #location /test {
        #   
        #root /home/your_account/your_project_name;
        #alias /home/your_account/your_project_name;
        #}
    }

    '''

step 4:
    sudo nginx -s reload
    sudo certbot --nginx
    
step 5:
    sudo apt-get install git-all
    sudo git clone ........
    
step 6:
    uwsgi -w main:app -s :3000
    
step 7: 
    Enjoy the game

