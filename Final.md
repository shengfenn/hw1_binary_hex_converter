```python
# 輸入10進位數字
decimal_number = input("輸入0-255之間的任意整數: ")
try:
    a = int(decimal_number)

    # 檢查是否在0-255之間
    if a < 0 or a > 255:
        print("請輸入範圍內的整數（0-255）")
    else:
        # 設定8個位置的值都是0的2進位list，由左而右分別代表2**7、2**6...2**0
        binary_converter_list = ['0', '0', '0', '0', '0', '0', '0', '0']

        # 將輸入的數字轉變成2的次方相加的形式，並在可寫成2**n*1之位置n以1替代0
        for n in range(7, -1, -1):
            if 2**n <= a:
                binary_converter_list[n] = '1'
                a = a - 2**n

        # 輸出轉換成2進位數字的結果
        binary_converter = ''.join(binary_converter_list[::-1])
        print("2進位數字:", int(binary_converter))
        
        #設定兩個位置的值為0的16進位list
        c = ['0','0']

        #將2進位轉換後的結果拿過來
        d = ''.join(binary_converter_list[::-1])

        #分別計算c[0]和c[1]的值，且轉換10-15為A-F
        for i in range(2):
            c[i] = str(int(d[4*i])*8 + int(d[4*i+1])*4 + int(d[4*i+2])*2 + int(d[4*i+3]))
            if c[i] == '10' :
                c[i] = 'A'
            elif c[i] == '11' :
                c[i] = 'B'
            elif c[i] == '12' :
                c[i] = 'C'
            elif c[i] == '13' :
                c[i] = 'D'
            elif c[i] == '14' :
                c[i] = 'E'
            elif c[i] == '15' :
                c[i] = 'F'
            elif c[i] == '0' :
                c[i] = '0'
        if c[0] == '0' :
            c.pop(0)
        #輸出轉換成16進位的結果
        hexadecimal_converter = ''.join(c)
        print("16進位數字:", hexadecimal_converter)
except:
    print("無法運算，請輸入整數")






```

    輸入0-255之間的任意整數:  798
    

    請輸入範圍內的整數（0-255）
    
