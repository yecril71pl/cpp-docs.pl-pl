---
title: Wskaźniki pierwotneC++()
description: Jak używać wskaźników surowych w programieC++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 2dbb4f11fc0c08578e82371e8df77e9643313879
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077150"
---
# <a name="raw-pointers-c"></a>Wskaźniki pierwotneC++()

Wskaźnik jest typem zmiennej, która przechowuje adres obiektu w pamięci i służy do uzyskiwania dostępu do tego obiektu. *Surowy wskaźnik* jest wskaźnikiem, którego okres istnienia nie jest kontrolowany przez obiekt hermetyzowany, taki jak [inteligentny wskaźnik](smart-pointers-modern-cpp.md). Do wskaźnika pierwotnego można przypisać adres innej zmiennej niebędącej wskaźnikiem lub może być przypisana wartość [nullptr](nullptr.md). Wskaźnik, który nie ma przypisanej wartości, zawiera dane losowe.

Wskaźnik może być również *odwołuje* się do pobrania wartości obiektu, który wskazuje. *Operator dostępu do elementów członkowskich* zapewnia dostęp do elementów członkowskich obiektu.

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

Wskaźnik może wskazywać na obiekt z określonym typem lub do typu **void**. Gdy program alokuje nowy obiekt na [stercie](https://wikipedia.org/wiki/Heap) w pamięci, otrzymuje adres tego obiektu w postaci wskaźnika. Takie wskaźniki są nazywane *wskaźnikami będącymi właścicielem*; wskaźnik będący właścicielem (lub jego kopia) musi być używany do jawnego usuwania obiektu przystosowanego sterty, gdy nie jest już wymagany. Nie można usunąć pamięci w wyniku *przecieku pamięci* i renderowanie tej lokalizacji pamięci jako niedostępnej dla żadnego innego programu na komputerze. Aby uzyskać więcej informacji, zobacz [Operatory New i DELETE](new-and-delete-operators.md).

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

Wskaźnik (jeśli nie jest zadeklarowany jako **const**) można zwiększyć lub zmniejszyć, tak aby wskazywał nową lokalizację w pamięci. Jest to nazywane *arytmetyką wskaźnika* i jest używany w programowaniu w stylu języka C do iteracji elementów w tablicach lub w innych strukturach danych. Nie można nawiązać wskaźnika **stałej** w celu wskazywania innej lokalizacji pamięci, a w tym sensie jest to bardzo podobne do [odwołania](references-cpp.md). Aby uzyskać więcej informacji, zobacz [wskaźniki const i volatile](const-and-volatile-pointers.md).

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

W 64-bitowych systemach operacyjnych wskaźnik ma rozmiar 64 bitów; rozmiar wskaźnika systemu określa ilość pamięci, jaką może mieć adres. Wszystkie kopie wskaźnika wskazują tę samą lokalizację w pamięci. Wskaźniki (wraz z odwołaniami) są szeroko używane C++ do przekazywania większych obiektów do i z funkcji, ponieważ zwykle jest znacznie bardziej wydajne, aby skopiować adres 64-bitowy obiektu, niż kopiowanie całego obiektu. Podczas definiowania funkcji Określ parametry wskaźnika jako **const** , chyba że zamierzasz, aby funkcja modyfikował obiekt. Ogólnie rzecz biorąc, odwołania **stałe** są preferowanym sposobem przekazywania obiektów do funkcji, chyba że wartość obiektu może być **nullptr**.

[Wskaźniki do funkcji](#pointers_to_functions) umożliwiają przekazywanie funkcji do innych funkcji i są używane do "wywołania zwrotne" w programowaniu w stylu języka C. Nowoczesne C++ używa [wyrażeń lambda](lambda-expressions-in-cpp.md) do tego celu.

## <a name="initialization-and-member-access"></a>Inicjowanie i dostęp do elementów członkowskich

Poniższy przykład pokazuje, jak zadeklarować surowy wskaźnik i zainicjować go z obiektem przydzielonym na stosie, a następnie jak go używać. Przedstawiono w nim również kilka zagrożeń związanych z nieprzetworzonymi wskaźnikami. (Pamiętaj, że jest to programowanie w stylu C, a C++nie nowoczesny!)

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

## <a name="pointer-arithmetic-and-arrays"></a>Arytmetyczne i tablice wskaźników

Wskaźniki i tablice są ściśle powiązane. Gdy tablica jest przenoszona przez wartość do funkcji, jest przenoszona jako wskaźnik do pierwszego elementu. Poniższy przykład ilustruje następujące ważne właściwości wskaźników i tablic:

- operator `sizeof` zwraca łączny rozmiar w bajtach tablicy
- Aby określić liczbę elementów, Podziel sumę bajtów o rozmiar jednego elementu
- gdy tablica jest przenoszona do funkcji, powoduje ona *zanikanie* do typu wskaźnika
- operator `sizeof` w przypadku zastosowania do wskaźnika zwraca rozmiar wskaźnika, 4 bajty w x86 lub 8 bajtów na x64

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

Niektóre operacje arytmetyczne mogą być wykonywane na wskaźnikach innych niż const, aby wskazywały na nową lokalizację pamięci. Wskaźnik może być zwiększany i zmniejszany przy użyciu operatorów **++** , **+=** , **-=** i **--** . Ta technika może być używana w tablicach i jest szczególnie przydatna w przypadku buforów danych, które nie są typu. Wartość typu **void\*** zwiększa się o rozmiar **char** (1 bajt). Wskaźnik o określonym typie zwiększa się według rozmiaru typu, na który wskazuje.

W poniższym przykładzie pokazano, jak można użyć arytmetycznego wskaźnika w celu uzyskania dostępu do poszczególnych pikseli w mapie bitowej w systemie Windows. Zwróć uwagę na użycie operatora **New** i **delete**oraz operator dereferencji.

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

## <a name="void-pointers"></a>void * wskaźniki

Wskaźnik do typu **void** po prostu wskazuje lokalizację w pamięci nieprzetworzonej. Czasami konieczne jest użycie wskaźników **void\*** , na przykład podczas przekazywania między C++ kodem a funkcjami języka C.

Gdy wpisany wskaźnik jest rzutowany na wskaźnik typu void, zawartość lokalizacji pamięci nie jest zmieniana, ale informacje o typie są tracone, dzięki czemu nie można wykonywać operacji zwiększania ani zmniejszania. Lokalizację pamięci można rzutować na przykład z MyClass * na void * i ponownie do MyClass *. Takie operacje są z natury podatne na błędy i wymagają dużej staranności, aby uniknąć błędów. Nowoczesne C++ odradza użycie wskaźników typu void, chyba że jest to absolutnie konieczne.

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
    for(char* c = static_cast<char*>(pvoid); pvoid < &pvoid + 1000; ++c)
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

W programowaniu w stylu języka C, wskaźniki funkcji są używane głównie do przekazywania funkcji do innych funkcji. W tym scenariuszu obiekt wywołujący może dostosować zachowanie funkcji bez jej modyfikowania. W nowoczesnych C++ [wyrażenia lambda](lambda-expressions-in-cpp.md) zapewniają taką samą funkcję, która zapewnia większe bezpieczeństwo typów i inne zalety.

Deklaracja wskaźnika funkcji określa sygnaturę, którą funkcja wskazywana musi mieć:

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

Poniższy przykład pokazuje funkcję `combine`, która przyjmuje jako parametr każdą funkcję, która akceptuje `std::string` i zwraca `std::string`. W zależności od funkcji, która jest przenoszona do `combine` dołączy lub dołączają ciąg.

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
[operator pośredni: *](indirection-operator-star.md)<br/>
[Operator Address-of: &](address-of-operator-amp.md)</br>
[Zapraszamy ponownie doC++](welcome-back-to-cpp-modern-cpp.md)
