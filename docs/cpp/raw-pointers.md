---
title: Nieprzetworzone wskaźniki (C++)
description: Jak używać surowych wskaźników w języku C++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 919447fcab123ce6b838391d3cc295fb8a8fe95e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374666"
---
# <a name="raw-pointers-c"></a>Nieprzetworzone wskaźniki (C++)

Wskaźnik jest typem zmiennej, która przechowuje adres obiektu w pamięci i jest używana do uzyskiwania dostępu do tego obiektu. *Nieprzetworzony wskaźnik* jest wskaźnikiem, którego okres istnienia nie jest kontrolowany przez obiekt hermetyzujący, taki jak [inteligentny wskaźnik.](smart-pointers-modern-cpp.md) Nieprzetworzony wskaźnik można przypisać adres innej zmiennej nie wskaźnik lub może być przypisany wartość [nullptr](nullptr.md). Wskaźnik, który nie został przypisany wartość zawiera losowe dane.

Wskaźnik może być również *wyłuskiwane,* aby pobrać wartość obiektu, który wskazuje na. *Operator dostępu elementu członkowskiego* zapewnia dostęp do elementów członkowskich obiektu.

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

Wskaźnik może wskazywać na wpisany obiekt lub **unieważnić**. Gdy program przydziela nowy obiekt na [stercie](https://wikipedia.org/wiki/Heap) w pamięci, odbiera adres tego obiektu w postaci wskaźnika. Takie wskaźniki są nazywane *wskaźnikami posiadania;* wskaźnik będący właścicielem (lub jego kopia) musi służyć do jawnego usuwania obiektu przydzielonego stercie, gdy nie jest już potrzebny. Niepowodzenie usunięcia pamięci powoduje *przeciek pamięci* i powoduje, że lokalizacja pamięci jest niedostępna dla innego programu na komputerze. Aby uzyskać więcej informacji, zobacz [nowe i usuń operatory](new-and-delete-operators.md).

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

Wskaźnik (jeśli nie jest zadeklarowany jako **const)** może być zwiększany lub zmniejszany, tak aby wskazuje nową lokalizację w pamięci. Jest to nazywane *arytmetyki wskaźnika* i jest używany w programowaniu w stylu C do iteracji nad elementami w tablicach lub innych struktur danych. Wskaźnik **const** nie może być wskażąc na inną lokalizację pamięci i w tym sensie jest bardzo podobny do [odwołania](references-cpp.md). Aby uzyskać więcej informacji, zobacz [wskaźniki const i volatile](const-and-volatile-pointers.md).

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    const char* str = "Hello world";

    const int c = 1;
    const int* pconst = &c; // declare a non-const pointer to const int
    const int c2 = 2;
    pconst = &c2;  // OK pconst itself isn't const
    const int* const pconst2 = &c;
    // pconst2 = &c2; // Error! pconst2 is const.
```

W 64-bitowych systemach operacyjnych wskaźnik ma rozmiar 64 bitów; rozmiar wskaźnika systemu określa, ile pamięci adresowalnej może mieć. Wszystkie kopie wskaźnika wskazują tę samą lokalizację pamięci. Wskaźniki (wraz z odwołaniami) są szeroko używane w języku C++ do przekazywania większych obiektów do i z funkcji, ponieważ zwykle jest znacznie bardziej wydajne, aby skopiować adres 64-bitowy obiektu niż skopiować cały obiekt. Podczas definiowania funkcji należy określić parametry wskaźnika jako **const,** chyba że zamierzasz, aby funkcja zmodyfikować obiekt. Ogólnie rzecz biorąc, odwołania **const** są preferowanym sposobem przekazywania obiektów do funkcji, chyba że wartość obiektu może być **nullptr**.

[Wskaźniki do funkcji](#pointers_to_functions) umożliwiają funkcje, które mają być przekazywane do innych funkcji i są używane do "wywołania zwrotnego" w programowaniu w stylu C. Modern C++ używa [wyrażeń lambda](lambda-expressions-in-cpp.md) w tym celu.

## <a name="initialization-and-member-access"></a>Inicjowanie i dostęp do członków

W poniższym przykładzie pokazano, jak zadeklarować nieprzetworzony wskaźnik i zainicjować go z obiektem przydzielonym na stercie, a następnie jak go używać. Pokazuje również kilka niebezpieczeństw związanych z surowymi wskaźnikami. (Pamiętaj, że jest to programowanie w stylu C, a nie nowoczesne C ++!)

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
void func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
void func_B(MyClass mc)
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
    // Use new to allocate and initialize memory
    MyClass* pmc = new MyClass{ 108, "Nick" };

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
    func_A(mc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*mc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    delete(pmc); // don't forget to give memory back to operating system!
   // delete(pmc2); //crash! memory location was already deleted
}
```

## <a name="pointer-arithmetic-and-arrays"></a>Arytmetyka wskaźnika i tablice

Wskaźniki i tablice są ściśle ze sobą powiązane. Gdy tablica jest przekazywana przez wartość do funkcji, jest przekazywana jako wskaźnik do pierwszego elementu. W poniższym przykładzie przedstawiono następujące ważne właściwości wskaźników i tablic:

- `sizeof` operator zwraca całkowity rozmiar w bajtach tablicy
- aby określić liczbę elementów, podziel całkowite bajty przez rozmiar jednego elementu
- gdy tablica jest przekazywana do funkcji, *rozpada* się na typ wskaźnika
- `sizeof` operator po zastosowaniu do wskaźnika zwraca rozmiar wskaźnika, 4 bajty na x86 lub 8 bajtów na x64

```cpp
#include <iostream>

void func(int arr[], int length)
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

Niektóre operacje arytmetyczne mogą być wykonywane na wskaźnikach innych niż const, aby wskazać nową lokalizację pamięci. Wskaźnik może być zwiększany i zmniejszany za **++** **+=** pomocą **-=** **--** programu , i operatorów. Ta technika może być używana w tablicach i jest szczególnie przydatna w buforach danych nietypowych. **Void\* ** zwiększa się o rozmiar **char** (1 bajt). Wpisany wskaźnik zwiększa się o rozmiar typu, na który wskazuje.

W poniższym przykładzie pokazano, jak arytmetyka wskaźnika może służyć do uzyskiwania dostępu do poszczególnych pikseli w mapie bitowej w systemie Windows. Zwróć uwagę na użycie **nowego** i **usuń**, a operator wyłudnika.

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

    constexpr int bufferSize = 30000;
    unsigned char* buffer = new unsigned char[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned char* begin = &buffer[0];
    unsigned char* end = &buffer[0] + bufferSize;
    unsigned char* p = begin;
    constexpr int pixelWidth = 3;
    constexpr int borderWidth = 2;

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
        p++; // Increment one byte sizeof(unsigned char).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<char*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<char*>(&header), sizeof(header));
    wf.write(reinterpret_cast<char*>(begin), bufferSize);

    delete[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="void-pointers"></a>wskaźniki void*

Wskaźnik do **void** po prostu wskazuje na lokalizację pamięci nieprzetworzonej. Czasami konieczne jest użycie **wskaźników void,\* ** na przykład podczas przekazywania między kodem C++ i funkcjami C.

Gdy wpisany wskaźnik jest rzutowany na wskaźnik void, zawartość lokalizacji pamięci nie są zmieniane, ale informacje o typie jest tracona, tak, że nie można wykonywać operacji przyrostu lub dekrementacji. Lokalizacja pamięci może być rzutowany, na przykład, z MyClass* do void* i z powrotem do MyClass*. Takie operacje są z natury podatne na błędy i wymagają dużej starannej starannością, aby uniknąć błędów. Nowoczesne C++ zniechęca do korzystania z wskaźników void, chyba że jest to absolutnie konieczne.

```cpp

//func.c
void func(void* data, int length)
{
    char* c = (char*)(data);

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
    void func(void* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = new MyClass{10, "Marian"};
    void* p = static_cast<void*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator new to allocate untyped memory block
    void* pvoid = operator new(1000);
    char* pchar = static_cast<char*>(pvoid);
    for(char* c = pchar; c < pchar + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>Wskaźniki do funkcji

W programowaniu w stylu C wskaźniki funkcji są używane przede wszystkim do przekazywania funkcji do innych funkcji. W tym scenariuszu wywołującego można dostosować zachowanie funkcji bez modyfikowania go. W nowoczesnych C++ [wyrażenia lambda](lambda-expressions-in-cpp.md) zapewniają taką samą możliwość z większym bezpieczeństwem typu i innymi zaletami.

Deklaracja wskaźnika funkcji określa podpis, który musi mieć funkcja wskazywania:

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
void (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

Poniższy przykład przedstawia `combine` funkcję, która przyjmuje jako parametr `std::string` dowolną `std::string`funkcję, która akceptuje i zwraca . W zależności od funkcji, `combine` która jest przekazywana do niego będzie prepend lub dołączyć ciąg.

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

## <a name="see-also"></a>Zobacz też

[Inteligentne wskaźniki](smart-pointers-modern-cpp.md)
[Pośredni operator: *](indirection-operator-star.md)<br/>
[Operator Address-of: &](address-of-operator-amp.md)</br>
[Witamy z powrotem w języku C++](welcome-back-to-cpp-modern-cpp.md)
