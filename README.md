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
