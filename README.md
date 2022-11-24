# Pracktical-work-9

# Шифр простой перестановки
def split_len(seq, length):
    return [seq[i:i + length] for i in range(0, len(seq), length)]

def encode(key, plaintext):

    order = {
        int(val): num for num, val in enumerate(key)
    }

    ciphertext = ''
    for index in sorted(order.keys()):
        for part in split_len(plaintext, len(key)):
            try:
                ciphertext += part[order[index]]
            except IndexError:
                continue

    return ciphertext

# RSA
def encr(m):
    return(m ** e) % n

def decr(m):
    return(m ** d) % n

while True:
    print("Выберите шифр: ", "1.Шифр простой перестановки", "2.Шифр RSA", "3.Выход", sep='\n')
    menu = int(input())

    # Шифр простой перестановки
    if menu == 1:
        text = input("Введите строку фразу которую хотите зашифровать: ")
        key = input("Введите ключ: ")
        code_ = encode(key, text)
        print(f"Ваша фраза: {text}. Ваш ключ: {key}.")
        print(f"Закодированная фраза: {encode(key, text)}")
        # ввод: у вас продаётся славянский шкаф
        # ввод: 38152647
        # Вывод: ваа стякуосипясфаёвш снар к длй

    # RSA
    elif (menu == 2):

        p = 13
        q = 7
        e = 5
        d = 29
        n = p * q
        Fi = (p-1)*(q-1)

        mas = [2,17,55] # m1 m2 m3
        encrypt_mas = [] # тут будут храниться зашифрованные сообщения

        print(f"Исходные сообщения: {mas}")

        for m in mas:
            tp = encr(m)
            encrypt_mas.append(tp)
            print(f"Зашифрованные сообщения: {tp}")
        for m in encrypt_mas:
            print(f"Расшифрованные сообщения: {decr(m)}")
    elif (menu == 3):
        break
    else:
        print("Данного пункта меню нет")
