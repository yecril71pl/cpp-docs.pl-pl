---
title: this — wskaźnik
ms.date: 11/04/2016
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
ms.openlocfilehash: 586ed9d7e07165af71eeb2ee7ab22aba9570bcd3
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328880"
---
# <a name="this-pointer"></a>this — wskaźnik

**To** wskaźnik jest dostępny tylko w niestatycznej składowej funkcje wskaźnik **klasy**, **struktury**, lub **Unii** typu. Wskazuje na obiekt, dla którego funkcja członkowska jest wywoływana. Statyczne funkcje Członkowskie nie mają **to** wskaźnika.

## <a name="syntax"></a>Składnia

```
this
this->member-identifier
```

## <a name="remarks"></a>Uwagi

Obiekt **to** wskaźnik nie jest częścią obiektu; nie jest odzwierciedlana w wyniku **sizeof** instrukcji w obiekcie. Zamiast tego po wywołaniu funkcji niestatycznej składowej obiektu adres obiektu, jest przekazywany przez kompilator jako ukryty argument do funkcji. Na przykład poniższe wywołanie funkcji:

```cpp
myDate.setMonth( 3 );
```

może być interpretowany w ten sposób:

```cpp
setMonth( &myDate, 3 );
```

Adres obiektu jest dostępne z poziomu funkcji składowej jako **to** wskaźnika. Większości zastosowań **to** są niejawne. Jest legalne, chociaż trzeba jawnie użyć **to** przy odwoływaniu się do elementów członkowskich klasy. Na przykład:

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   this->month = mn;      // are equivalent
   (*this).month = mn;
}
```

Wyrażenie `*this` jest najczęściej używany do zwracania bieżącego obiektu z funkcji składowej:

```cpp
return *this;
```

**To** wskaźnik jest również używane do ochrony przed odwołanie do samego siebie:

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
>  Ponieważ **to** wskaźnik jest niemodyfikowalnymi, przydziały, aby **to** nie są dozwolone. Wcześniejszych implementacji C++ mogą przypisania do **to**.

Od czasu do czasu **to** bezpośrednio służy wskaźnika — na przykład, można manipulować danymi relacją struktury, gdy wymagany jest adres bieżący obiekt.

## <a name="example"></a>Przykład

```cpp
// this_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

class Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( const Buf & );
    void Display() { cout << buffer << endl; }

private:
    char*   buffer;
    size_t  sizeOfBuffer;
};

Buf::Buf( char* szBuffer, size_t sizeOfBuffer )
{
    sizeOfBuffer++; // account for a NULL terminator

    buffer = new char[ sizeOfBuffer ];
    if (buffer)
    {
        strcpy_s( buffer, sizeOfBuffer, szBuffer );
        sizeOfBuffer = sizeOfBuffer;
    }
}

Buf& Buf::operator=( const Buf &otherbuf )
{
    if( &otherbuf != this )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *this;
}

int main()
{
    Buf myBuf( "my buffer", 10 );
    Buf yourBuf( "your buffer", 12 );

    // Display 'my buffer'
    myBuf.Display();

    // assignment opperator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-this-pointer"></a>Typ tego wskaźnika

**To** w deklaracji funkcji, można zmodyfikować typu wskaźnika **const** i **volatile** słów kluczowych. Aby zadeklarować funkcję jako mające atrybuty co najmniej jednego z tych słów kluczowych, Dodaj słowa po liście argumentów funkcji.

Rozważmy następujący przykład:

```cpp
// type_of_this_pointer1.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

W poprzednim kodzie zadeklarowano funkcję członkowską `X`, w którym **to** wskaźnik jest traktowany jako **const** wskaźnik do **const** obiektu. Kombinacje *cv mod listy* opcje mogą być używane, ale zawsze zmodyfikować obiekt wskazywany przez **to**, a nie **to** wskaźnika jako takiego. W związku z tym, następująca deklaracja deklaruje funkcję `X`; **to** wskaźnik jest **const** wskaźnik do **const** obiektu:

```cpp
// type_of_this_pointer2.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

Typ **to** w składowej funkcji opisano przy użyciu następującej składni, gdzie *cv kwalifikator listy* jest określana na podstawie deklaratora funkcji elementu członkowskiego i może być **const**lub **volatile** (lub obie), a *typu klasy* jest nazwa klasy:

*Typ klasy [cv kwalifikator list]* **&#42; stała tym**

Innymi słowy **to** jest zawsze wskaźnika elementu const; nie może zostać przypisany.  **Const** lub **volatile** kwalifikatory użyty w deklaracji funkcji elementu członkowskiego dotyczy wskazywany przez wystąpienie klasy **to** w zakresie tej funkcji.

W poniższej tabeli opisano więcej informacji na temat działania tych modyfikatorów.

### <a name="semantics-of-this-modifiers"></a>Semantyka tej modyfikatorów

|Modyfikator|Znaczenie|
|--------------|-------------|
|**const**|Nie można zmienić element członkowski danych; Nie można wywołać funkcji elementów członkowskich, które nie są **const**.|
|**volatile**|Element członkowski danych jest ładowany z pamięci, każdym razem, gdy jest on dostępny; wyłącza niektóre optymalizację.|

Jest to błąd, aby przekazać **const** obiektu do funkcji składowej, która nie jest **const**. Podobnie, występuje błąd do przekazania **volatile** obiektu do funkcji składowej, która nie jest **volatile**.

Funkcje składowe są deklarowane jako **const** nie można zmienić element członkowski danych — w takie funkcje **to** wskaźnik jest wskaźnikiem do **const** obiektu.

> [!NOTE]
>  Konstruktory i destruktory nie można zadeklarować jako **const** lub **volatile**. Jednak mogą być wywoływane na **const** lub **volatile** obiektów.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)