---
title: Wskaźniki pierwotne (C++)
description: Jak używać wskaźników surowych w języku C++
ms.date: 04/21/2020
helpviewer_keywords:
- pointers [C++]
no-loc:
- ':::no-loc(void):::'
- ':::no-loc(nullptr):::'
- ':::no-loc(const):::'
- ':::no-loc(char):::'
- ':::no-loc(new):::'
- ':::no-loc(delete):::'
ms.openlocfilehash: 53679559888191fe7f2aad7cb5a70d607974ae96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233655"
---
# <a name="raw-pointers-c"></a>Wskaźniki pierwotne (C++)

*Wskaźnik* jest typem zmiennej. Przechowuje adres obiektu w pamięci i służy do uzyskiwania dostępu do tego obiektu. *Surowy wskaźnik* jest wskaźnikiem, którego okres istnienia nie jest kontrolowany przez obiekt hermetyzowany, taki jak [inteligentny wskaźnik](smart-pointers-modern-cpp.md). Do wskaźnika pierwotnego można przypisać adres innej zmiennej niebędącej wskaźnikiem lub może być przypisana wartość [:::no-loc(nullptr):::](:::no-loc(nullptr):::.md) . Wskaźnik, który nie ma przypisanej wartości, zawiera dane losowe.

Wskaźnik może być również *odwołuje* się do pobrania wartości obiektu, który wskazuje. *Operator dostępu do elementów członkowskich* zapewnia dostęp do elementów członkowskich obiektu.

```cpp
    int* p = :::no-loc(nullptr):::; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address
```

Wskaźnik może wskazywać na obiekt z określonym typem lub do **`:::no-loc(void):::`** . Gdy program alokuje obiekt na [stercie](https://wikipedia.org/wiki/Heap) w pamięci, otrzymuje adres tego obiektu w postaci wskaźnika. Takie wskaźniki są nazywane *wskaźnikami będącymi właścicielami*. Wskaźnik będący właścicielem (lub jego kopia) musi być używany do bezpośredniego zwolnienia obiektu przystosowanego do sterty, gdy nie jest już wymagany. Nie można zwolnić pamięci z powodu *przecieku pamięci*, a ta lokalizacja pamięci jest niedostępna dla żadnego innego programu na komputerze. Pamięć przydzielone za pomocą **`:::no-loc(new):::`** musi być zwolniona przy użyciu **`:::no-loc(delete):::`** ** :::no-loc(delete)::: \[ **(lub). Aby uzyskać więcej informacji, zobacz [ :::no-loc(new)::: i :::no-loc(delete)::: Operatory](:::no-loc(new):::-and-:::no-loc(delete):::-operators.md).

```cpp
    MyClass* mc = :::no-loc(new)::: MyClass(); // allocate object on the heap
    mc->print(); // access class member
    :::no-loc(delete)::: mc; // :::no-loc(delete)::: object (please don't forget!)
```

Wskaźnik (jeśli nie jest zadeklarowany jako **`:::no-loc(const):::`** ) można zwiększyć lub zmniejszyć do momentu w innej lokalizacji w pamięci. Ta operacja jest nazywana *arytmetyczną wskaźnikiem*. Jest on używany w programowaniu w stylu języka C do iteracji nad elementami w tablicach lub w innych strukturach danych. **`:::no-loc(const):::`** Nie można nawiązać wskaźnika w celu wskazywania innej lokalizacji pamięci, a w tym sensie jest podobna do [odwołania](references-cpp.md). Aby uzyskać więcej informacji, zobacz [ :::no-loc(const)::: i wskaźniki lotne](:::no-loc(const):::-and-volatile-pointers.md).

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    :::no-loc(const)::: :::no-loc(char):::* str = "Hello world";

    :::no-loc(const)::: int c = 1;
    :::no-loc(const)::: int* p:::no-loc(const)::: = &c; // declare a non-:::no-loc(const)::: pointer to :::no-loc(const)::: int
    :::no-loc(const)::: int c2 = 2;
    p:::no-loc(const)::: = &c2;  // OK p:::no-loc(const)::: itself isn't :::no-loc(const):::
    :::no-loc(const)::: int* :::no-loc(const)::: p:::no-loc(const):::2 = &c;
    // p:::no-loc(const):::2 = &c2; // Error! p:::no-loc(const):::2 is :::no-loc(const):::.
```

W 64-bitowych systemach operacyjnych wskaźnik ma rozmiar 64 bitów. Rozmiar wskaźnika systemu określa ilość pamięci, jaką może mieć adres. Wszystkie kopie wskaźnika wskazują tę samą lokalizację w pamięci. Wskaźniki (wraz z odwołaniami) są szeroko używane w języku C++ do przekazywania większych obiektów do i z funkcji. Dzieje się tak, ponieważ często bardziej wydajne jest skopiowanie adresu obiektu niż kopiowanie całego obiektu. Podczas definiowania funkcji należy określić parametry wskaźnika jako, **`:::no-loc(const):::`** chyba że funkcja modyfikuje obiekt. Ogólnie rzecz biorąc, **`:::no-loc(const):::`** odwołania są preferowanym sposobem przekazywania obiektów do funkcji, chyba że wartość obiektu może być niemożliwa **`:::no-loc(nullptr):::`** .

[Wskaźniki do funkcji](#pointers_to_functions) umożliwiają przekazywanie funkcji do innych funkcji i są używane do "wywołania zwrotne" w programowaniu w stylu języka C. W tym celu w nowoczesnych językach C++ są stosowane [wyrażenia lambda](lambda-expressions-in-cpp.md) .

## <a name="initialization-and-member-access"></a>Inicjowanie i dostęp do elementów członkowskich

Poniższy przykład pokazuje, jak zadeklarować, zainicjować i używać surowego wskaźnika. Jest on inicjowany przy użyciu **`:::no-loc(new):::`** , aby wskazywał obiekt przydzielony na stosie, który należy jawnie **`:::no-loc(delete):::`** . W przykładzie przedstawiono również kilka zagrożeń związanych z nieprzetworzonymi wskaźnikami. (Pamiętaj, że ten przykład to programowanie w stylu C i nie nowoczesny C++)

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    :::no-loc(void)::: print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
:::no-loc(void)::: func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
:::no-loc(void)::: func_B(MyClass mc)
{
    // mc here is a regular object, not a pointer.
    // Use the "." operator to access members.
    // This statement modifies only the local copy of mc.
    mc.num = 21;
    std::cout << "Local copy of mc:";
    mc.print(); // "Erika, 21"
}


int main()
{
    // Use the * operator to declare a pointer type
    // Use :::no-loc(new)::: to allocate and initialize memory
    MyClass* pmc = :::no-loc(new)::: MyClass{ 108, "Nick" };

    // Prints the memory address. Usually not what you want.
    std:: cout << pmc << std::endl;

    // Copy the pointed-to object by dereferencing the pointer
    // to access the contents of the memory location.
    // mc is a separate object, allocated here on the stack
    MyClass mc = *pmc;

    // Declare a pointer that points to mc using the addressof operator
    MyClass* pcopy = &mc;

    // Use the -> operator to access the object's public members
    pmc->print(); // "Nick, 108"

    // Copy the pointer. Now pmc and pmc2 point to same object!
    MyClass* pmc2 = pmc;

    // Use copied pointer to modify the original object
    pmc2->name = "Erika";
    pmc->print(); // "Erika, 108"
    pmc2->print(); // "Erika, 108"

    // Pass the pointer to a function.
    func_A(pmc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*pmc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    :::no-loc(delete):::(pmc); // don't forget to give memory back to operating system!
   // :::no-loc(delete):::(pmc2); //crash! memory location was already :::no-loc(delete):::d
}
```

## <a name="pointer-arithmetic-and-arrays"></a>Arytmetyczne i tablice wskaźników

Wskaźniki i tablice są ściśle powiązane. Gdy tablica jest przenoszona przez wartość do funkcji, jest ona przenoszona jako wskaźnik do pierwszego elementu. Poniższy przykład ilustruje następujące ważne właściwości wskaźników i tablic:

- **`sizeof`** operator zwraca łączny rozmiar w bajtach tablicy
- Aby określić liczbę elementów, Podziel sumę bajtów o rozmiar jednego elementu
- gdy tablica jest przenoszona do funkcji, powoduje ona *zanikanie* do typu wskaźnika
- **`sizeof`** operator w przypadku zastosowania do wskaźnika zwraca rozmiar wskaźnika, 4 bajty w x86 lub 8 bajtów na x64

```cpp
#include <iostream>

:::no-loc(void)::: func(int arr[], int length)
{
    // returns pointer size. not useful here.
    size_t test = sizeof(arr);

    for(int i = 0; i < length; ++i)
    {
        std::cout << arr[i] << " ";
    }
}

int main()
{

    int i[5]{ 1,2,3,4,5 };
    // sizeof(i) = total bytes
    int j = sizeof(i) / sizeof(i[0]);
    func(i,j);
}
```

Niektóre operacje arytmetyczne mogą być używane w przypadku braku :::no-loc(const)::: wskaźników, aby wskazywały na inną lokalizację w pamięci. Wskaźniki są zwiększane i zmniejszane przy użyciu **++** **+=** operatorów, **-=** i **--** . Ta technika może być używana w tablicach i jest szczególnie przydatna w przypadku buforów danych, które nie są typu. Wartość jest **:::no-loc(void):::\*** zwiększana o rozmiar **`:::no-loc(char):::`** (1 bajt). Wskaźnik o określonym typie jest zwiększany o rozmiar typu, na który wskazuje.

W poniższym przykładzie pokazano, jak można użyć arytmetycznego wskaźnika w celu uzyskania dostępu do poszczególnych pikseli w mapie bitowej w systemie Windows. Zwróć uwagę na użycie **`:::no-loc(new):::`** operatora and i **`:::no-loc(delete):::`** operator dereferencji.

```cpp
#include <Windows.h>
#include <fstream>

using namespace std;

int main()
{

    BITMAPINFOHEADER header;
    header.biHeight = 100; // Multiple of 4 for simplicity.
    header.biWidth = 100;
    header.biBitCount = 24;
    header.biPlanes = 1;
    header.biCompression = BI_RGB;
    header.biSize = sizeof(BITMAPINFOHEADER);

    :::no-loc(const):::expr int bufferSize = 30000;
    unsigned :::no-loc(char):::* buffer = :::no-loc(new)::: unsigned :::no-loc(char):::[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned :::no-loc(char):::* begin = &buffer[0];
    unsigned :::no-loc(char):::* end = &buffer[0] + bufferSize;
    unsigned :::no-loc(char):::* p = begin;
    :::no-loc(const):::expr int pixelWidth = 3;
    :::no-loc(const):::expr int borderWidth = 2;

    while (p < end)
    {
            // Is top or bottom edge?
        if ((p < begin + header.biWidth * pixelWidth * borderWidth)
            || (p > end - header.biWidth * pixelWidth * borderWidth)
            // Is left or right edge?
            || (p - begin) % (header.biWidth * pixelWidth) < (borderWidth * pixelWidth)
            || (p - begin) % (header.biWidth * pixelWidth) > ((header.biWidth - borderWidth) * pixelWidth))
        {
            *p = 0x0; // Black
        }
        else
        {
            *p = 0xC3; // Gray
        }
        p++; // Increment one byte sizeof(unsigned :::no-loc(char):::).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<:::no-loc(char):::*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<:::no-loc(char):::*>(&header), sizeof(header));
    wf.write(reinterpret_cast<:::no-loc(char):::*>(begin), bufferSize);

    :::no-loc(delete):::[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="no-locvoid-pointers"></a>:::no-loc(void):::* wskaźniki

Wskaźnik **`:::no-loc(void):::`** po prostu wskazuje lokalizację w pamięci nieprzetworzonej. Czasami konieczne jest użycie **:::no-loc(void):::\*** wskaźników, na przykład podczas przekazywania między kodem C++ i funkcjami języka C.

Gdy określony wskaźnik jest rzutowany na :::no-loc(void)::: wskaźnik, zawartość lokalizacji pamięci nie jest zmieniana. Jednak informacje o typie są tracone, dzięki czemu nie można wykonywać operacji zwiększania ani zmniejszania. Lokalizację pamięci można rzutować na przykład z `MyClass*` **`:::no-loc(void):::*`** i z powrotem do `MyClass*` . Takie operacje są z natury podatne na błędy i wymagają dużej uwagi do :::no-loc(void)::: błędów. Nowoczesne C++ odradza użycie :::no-loc(void)::: wskaźników w prawie całych okolicznościach.

```cpp

//func.c
:::no-loc(void)::: func(:::no-loc(void):::* data, int length)
{
    :::no-loc(char):::* c = (:::no-loc(char):::*)(data);

    // fill in the buffer with data
    for (int i = 0; i < length; ++i)
    {
        *c = 0x41;
        ++c;
    }
}

// main.cpp
#include <iostream>

extern "C"
{
    :::no-loc(void)::: func(:::no-loc(void):::* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    :::no-loc(void)::: print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = :::no-loc(new)::: MyClass{10, "Marian"};
    :::no-loc(void):::* p = static_cast<:::no-loc(void):::*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator :::no-loc(new)::: to allocate untyped memory block
    :::no-loc(void):::* p:::no-loc(void)::: = operator :::no-loc(new):::(1000);
    :::no-loc(char):::* p:::no-loc(char)::: = static_cast<:::no-loc(char):::*>(p:::no-loc(void):::);
    for(:::no-loc(char):::* c = p:::no-loc(char):::; c < p:::no-loc(char)::: + 1000; ++c)
    {
        *c = 0x00;
    }
    func(p:::no-loc(void):::, 1000);
    :::no-loc(char)::: ch = static_cast<:::no-loc(char):::*>(p:::no-loc(void):::)[0];
    std::cout << ch << std::endl; // 'A'
    operator :::no-loc(delete):::(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>Wskaźniki do funkcji

W programowaniu w stylu języka C, wskaźniki funkcji są używane głównie do przekazywania funkcji do innych funkcji. Ta technika umożliwia obiektowi wywołującemu dostosowanie zachowania funkcji bez jej modyfikowania. W nowoczesnych językach C++ [wyrażenia lambda](lambda-expressions-in-cpp.md) zapewniają taką samą funkcję, która zapewnia większe bezpieczeństwo typów i inne zalety.

Deklaracja wskaźnika funkcji określa sygnaturę, którą funkcja wskazywana musi mieć:

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
:::no-loc(void)::: (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

Poniższy przykład pokazuje funkcję `combine` , która przyjmuje jako parametr każda funkcja, która akceptuje `std::string` i zwraca `std::string` . W zależności od funkcji, która jest przenoszona do `combine` , dołącza lub dołącza ciąg.

```cpp
#include <iostream>
#include <string>

using namespace std;

string base {"hello world"};

string append(string s)
{
    return base.append(" ").append(s);
}

string prepend(string s)
{
    return s.append(" ").append(base);
}

string combine(string s, string(*g)(string a))
{
    return (*g)(s);
}

int main()
{
    cout << combine("from MSVC", append) << "\n";
    cout << combine("Good morning and", prepend) << "\n";
}
```

## <a name="see-also"></a>Zobacz także

[Inteligentne wskaźniki](smart-pointers-modern-cpp.md) 
 [Operator pośredni: *](indirection-operator-star.md)<br/>
[Operator Address-of: &](address-of-operator-amp.md)</br>
[Witamy ponownie w języku C++](welcome-back-to-cpp-modern-cpp.md)
