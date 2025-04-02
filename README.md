# 5.1 Функция приветствия
def hello(name: 'имя пользователя' = None):
    """Выводит 'Hello, World' или 'Hello, {name}', если передан параметр."""
    return f"Hello, {name}" if name else "Hello, World"

# 5.2 Функция арифметических операций
def arithmetic(a: 'первое число', b: 'второе число', operation: 'операция'): 
    """Выполняет указанную арифметическую операцию над числами."""
    if operation == '+':
        return a + b
    elif operation == '-':
        return a - b
    elif operation == '*':
        return a * b
    elif operation == '/':
        return a / b if b != 0 else 'Деление на ноль'
    else:
        return "Неизвестная операция"

# 5.3 Функция расчета параметров квадрата
def square(side: 'сторона квадрата'):
    """Возвращает периметр, площадь и диагональ квадрата."""
    from math import sqrt
    return (4 * side, side ** 2, sqrt(2) * side)

# 5.4 Функция определения времени года по месяцу
def season(month: 'номер месяца (1-12)'):
    """Возвращает время года по номеру месяца."""
    if month in [12, 1, 2]:
        return "зима"
    elif month in [3, 4, 5]:
        return "весна"
    elif month in [6, 7, 8]:
        return "лето"
    elif month in [9, 10, 11]:
        return "осень"
    else:
        return "Некорректный номер месяца"

# 5.5 Функция расчета банковского вклада
def bank(a: 'начальная сумма', years: 'количество лет'):
    """Возвращает сумму вклада через заданное число лет под 10% годовых."""
    for _ in range(years):
        a += a * 0.1
    return round(a, 2)

# Тестирование функций
if __name__ == "__main__":
    print(hello())  # Hello, World
    print(hello("Alice"))  # Hello, Alice
    
    print(arithmetic(10, 5, '+'))  # 15
    print(arithmetic(10, 5, '/'))  # 2.0
    print(arithmetic(10, 0, '/'))  # Деление на ноль
    print(arithmetic(10, 5, '^'))  # Неизвестная операция
    
    print(square(4))  # (16, 16, 5.6568...)
    
    print(season(3))  # весна
    print(season(13))  # Некорректный номер месяца
    
    print(bank(1000, 5))  # 1610.51


    # 5.1 Класс Автор
class Author:
    def __init__(self, full_name: 'ФИО автора', country: 'Страна происхождения'):
        """Создает автора с ФИО и страной."""
        self.full_name = full_name
        self.country = country
    
    def display_info(self):
        """Выводит информацию об авторе."""
        print(f"Автор: {self.full_name}, Страна: {self.country}")

# Создание списка авторов
n = int(input("Введите количество авторов: "))
authors = []
for _ in range(n):
    name = input("Введите ФИО автора: ")
    country = input("Введите страну автора: ")
    authors.append(Author(name, country))

print("\nВсе авторы:")
for author in authors:
    author.display_info()

print("\nРусские авторы:")
for author in authors:
    if author.country.lower() == "россия":
        author.display_info()


# 5.2 Класс Книга
class Book:
    def __init__(self, title: 'Название книги'):
        """Создает книгу с заданным названием."""
        self.title = title
        self.__content = []
        print(f"Книга '{self.title}' создана")
    
    def __del__(self):
        """Выводит сообщение при удалении книги."""
        print(f"Книга '{self.title}' удалена")
    
    # 5.3 Методы для работы с содержанием
    def add_work(self, work: 'Название произведения'):
        """Добавляет произведение в содержание книги."""
        self.__content.append(work)
    
    def get_work_count(self):
        """Возвращает количество произведений в книге."""
        return len(self.__content)
    
    # 5.4 Метод вывода информации о книге
    def display_info(self):
        """Выводит информацию о книге и ее содержании."""
        print(f"Книга: {self.title}")
        print("Содержание:")
        for i, work in enumerate(self.__content, 1):
            print(f"{i}) {work}")

# Тестирование класса Book
book = Book("Антология рассказов")
book.add_work("Рассказ 1")
book.add_work("Рассказ 2")
book.display_info()
print(f"Количество произведений: {book.get_work_count()}")

del book
