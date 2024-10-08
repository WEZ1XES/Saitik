from flask import Flask
import random

app = Flask(__name__)

# Список фактов о технологической зависимости
facts_list = [
    "Большинство людей, страдающих технологической зависимостью, испытывают сильный стресс, когда они находятся вне зоны покрытия сети или не могут использовать свои устройства.",
    "Согласно исследованию, проведенному в 2018 году, более 50% людей в возрасте от 18 до 34 лет считают себя зависимыми от своих смартфонов.",
    "Изучение технологической зависимости является одной из наиболее актуальных областей научных исследований в настоящее время.",
    "Согласно исследованию, проведенному в 2019 году, более 60% людей отвечают на рабочие сообщения в своих смартфонах в течение 15 минут после того, как они вышли с работы.",
    "Один из способов борьбы с технологической зависимостью - это поиск занятий, которые приносят удовольствие и улучшают настроение.",
    "Илон Маск утверждает, что социальные сети созданы для того, чтобы удерживать нас внутри платформы, чтобы мы тратили как можно больше времени на просмотр контента.",
    "Илон Маск также выступает за регулирование социальных сетей и защиту личных данных пользователей. Он утверждает, что социальные сети собирают огромное количество информации о нас, которую потом можно использовать для манипулирования нашими мыслями и поведением.",
    "Социальные сети имеют как позитивные, так и негативные стороны, и мы должны быть более осознанными в использовании этих платформ."
]

@app.route('/')
def home():
    return '''
    <h1>Добро пожаловать!</h1>
    <p>Выберите действие:</p>
    <ul>
        <li><a href="/random_fact">Посмотреть случайный факт</a></li>
        <li><a href="/generate_password">Генератор случайного пароля</a></li>
        <li><a href="/random_number">Случайное число</a></li>
        <li><a href="/about">Обо мне</a></li>
        <li><a href="/smile">Получить улыбку</a></li>
    </ul>
    '''

@app.route('/random_fact')
def random_fact():
    fact = random.choice(facts_list)
    return f'''
    <h2>{fact}</h2>
    <a href="/">Назад на главную</a>
    '''

@app.route('/generate_password')
def generate_password():
    characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()"
    password = ''.join(random.choice(characters) for _ in range(12))
    return f'''
    <h2>Ваш случайный пароль: {password}</h2>
    <a href="/">Назад на главную</a>
    '''

@app.route('/random_number')
def random_number():
    number = random.randint(1, 100)
    return f'''
    <h2>Ваше случайное число: {number}</h2>
    <a href="/">Назад на главную</a>
    '''

@app.route("/about")
def about():
    return '''
    <h2>ПРИВЕТ,КАК ТВОИ ДЕЛА?!</h2>
    <a href="/">Назад на главную</a>
    '''

@app.route("/smile")
def smile():
    return '''
    <h2>ВОТ ТВОЯ УЛЫБКА! 😊</h2>
    <a href="/">Назад на главную</a>
    '''

if name == "main":
    app.run(debug=True)
