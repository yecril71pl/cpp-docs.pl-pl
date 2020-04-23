---
title: Nieprzetworzone wskaźniki (C++)
description: Jak używać surowych wskaźników w języku C++
ms.date: 04/21/2020
helpviewer_keywords:
- pointers [C++]
no-loc:
- void
- nullptr
- const
- char
- new
- delete
ms.openlocfilehash: 8ba188154d7395ce7be3878fa9dbee2fde08a130
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032099"
---
# <a name="raw-pointers-c"></a>Nieprzetworzone wskaźniki (C++)

Wskaźnik *pointer* jest typem zmiennej. Przechowuje adres obiektu w pamięci i jest używany do uzyskiwania dostępu do tego obiektu. *Nieprzetworzony wskaźnik* jest wskaźnikiem, którego okres istnienia nie jest kontrolowany przez obiekt hermetyzujący, taki jak [inteligentny wskaźnik](smart-pointers-modern-cpp.md). Nieprzetworzonemu wskaźnikowi można przypisać adres innej zmiennej niebędącej wskaźnikiem [nullptr](nullptr.md)lub można przypisać mu wartość . Wskaźnik, który nie został przypisany wartość zawiera losowe dane.

Wskaźnik może być również *wyłuskiwane,* aby pobrać wartość obiektu, który wskazuje na. *Operator dostępu elementu członkowskiego* zapewnia dostęp do elementów członkowskich obiektu.

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address
```

Wskaźnik może wskazywać na wpisany **void** obiekt lub na . Gdy program przydziela obiekt na [stercie](https://wikipedia.org/wiki/Heap) w pamięci, odbiera adres tego obiektu w postaci wskaźnika. Takie wskaźniki są nazywane *wskaźnikami właścicielami*. Wskaźnik będący właścicielem (lub jego kopia) musi służyć do jawnego zwolnienia obiektu przydzielonego stercie, gdy nie jest już potrzebny. Niepowodzenie zwolnienia pamięci powoduje *przeciek pamięci*i powoduje, że lokalizacja pamięci jest niedostępna dla innego programu na komputerze. Pamięć przydzielona przy **new** użyciu **delete** musi zostać zwolniona przy użyciu (lub ** delete \[]**). Aby uzyskać więcej informacji, zobacz [ new delete i operatorów](new-and-delete-operators.md).

```cpp
    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

Wskaźnik (jeśli nie jest zadeklarowany jako) **const** może być zwiększany lub zmniejszany, aby wskazać inną lokalizację w pamięci. Ta operacja jest nazywana *arytmetyką wskaźnika*. Jest on używany w programowaniu w stylu C do iteracji nad elementami w tablicach lub innych struktur danych. Nie **const** można wskazać innej lokalizacji pamięci i w tym sensie jest podobny do [odwołania.](references-cpp.md) Aby uzyskać więcej informacji, zobacz [ const i wskaźniki nietrwałe](const-and-volatile-pointers.md).

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

W 64-bitowych systemach operacyjnych wskaźnik ma rozmiar 64 bitów. Rozmiar wskaźnika systemu określa, ile pamięci adresowalnej może mieć. Wszystkie kopie wskaźnika wskazują tę samą lokalizację pamięci. Wskaźniki (wraz z odwołaniami) są szeroko używane w języku C++ do przekazywania większych obiektów do i z funkcji. To dlatego, że często bardziej efektywne jest kopiowanie adresu obiektu niż kopiowanie całego obiektu. Podczas definiowania funkcji należy określić parametry wskaźnika jako, **const** chyba że funkcja ma zmodyfikować obiekt. Ogólnie rzecz **const** biorąc, odwołania są preferowanym sposobem przekazywania obiektów do **nullptr** funkcji, chyba że wartość obiektu może być ewentualnie .

[Wskaźniki do funkcji](#pointers_to_functions) umożliwiają funkcje, które mają być przekazywane do innych funkcji i są używane do "wywołania zwrotnego" w programowaniu w stylu C. Modern C++ używa [wyrażeń lambda](lambda-expressions-in-cpp.md) w tym celu.

## <a name="initialization-and-member-access"></a>Inicjowanie i dostęp do członków

W poniższym przykładzie pokazano, jak zadeklarować, zainicjować i użyć nieprzetworzonego wskaźnika. Jest inicjowany **new** przy użyciu wskaż obiekt przydzielony na **delete** stercie, który należy jawnie . W przykładzie pokazano również kilka niebezpieczeństw związanych z surowymi wskaźnikami. (Pamiętaj, że w tym przykładzie jest programowanie w stylu C, a nie nowoczesne C ++!)

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
    func_A(pmc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*pmc);
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

Niektóre operacje arytmetyczne mogą byćconst używane na wskaźnikach innych niż wskaźniki, aby wskazać inną lokalizację pamięci. Wskaźniki są zwiększane i zmniejszane przy **++** użyciu **+=** **-=** programu **--** , i operatorów. Ta technika może być używana w tablicach i jest szczególnie przydatna w buforach danych nietypowych. A ** void ** jest zwiększany o rozmiar **char** (1 bajt). Wpisany wskaźnik zostanie wzmocniony o rozmiar typu, na który wskazuje.

W poniższym przykładzie pokazano, jak arytmetyka wskaźnika może służyć do uzyskiwania dostępu do poszczególnych pikseli w mapie bitowej w systemie Windows. Należy zwrócić **new** uwagę **delete** na użycie i , i operatora wyłudnika.

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

## <a name="opno-locvoid-pointers"></a>void* wskaźniki

Wskaźnik wskazujący **void** po prostu lokalizację pamięci nieprzetworzonej. Czasami jest konieczne użycie ** void ** wskaźników, na przykład podczas przekazywania między kodem C++ i funkcjami C.

Gdy wpisany wskaźnik jest void rzutowany na wskaźnik, zawartość lokalizacji pamięci pozostaje niezmieniona. Jednak informacje o typie są tracone, dzięki czemu nie można wykonać operacji przyrostu lub dekrementacji. Lokalizację pamięci można rzutować, na `MyClass*` `void*` przykład, od `MyClass*`do i z powrotem do . Takie operacje są z natury podatne na błędy i wymagają dużej starannej starannością, aby uniknąć błędów. Nowoczesne C++ zniechęca do void korzystania z wskaźników w prawie wszystkich okolicznościach.

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

W programowaniu w stylu C wskaźniki funkcji są używane przede wszystkim do przekazywania funkcji do innych funkcji. Ta technika umożliwia wywołującemu dostosować zachowanie funkcji bez modyfikowania go. W nowoczesnych C++ [wyrażenia lambda](lambda-expressions-in-cpp.md) zapewniają taką samą możliwość z większym bezpieczeństwem typu i innymi zaletami.

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

Poniższy przykład przedstawia `combine` funkcję, która przyjmuje jako parametr `std::string` dowolną `std::string`funkcję, która akceptuje i zwraca . W zależności od funkcji, `combine`która jest przekazywana do , to albo poprzedza lub dołącza ciąg.

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
