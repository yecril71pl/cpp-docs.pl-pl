---
title: :::no-loc(this):::przytrzymaj
description: :::no-loc(this):::Wskaźnik jest wygenerowanym przez kompilator wskaźnikiem do bieżącego obiektu w niestatycznych funkcjach składowych.
ms.date: 01/22/2020
f1_keywords:
- :::no-loc(this):::_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- 'pointers, to :::no-loc(class)::: instance'
- ':::no-loc(this)::: pointer'
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- ':::no-loc(this):::'
- ':::no-loc(class):::'
- ':::no-loc(struct):::'
- ':::no-loc(union):::'
- ':::no-loc(sizeof):::'
- ':::no-loc(const):::'
- ':::no-loc(volatile):::'
ms.openlocfilehash: c851beaba7fe1091ffd7827714f90307303058c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225829"
---
# <a name="no-locthis-pointer"></a>:::no-loc(this):::przytrzymaj

**`:::no-loc(this):::`** Wskaźnik jest dostępny tylko w obrębie niestatycznych funkcji składowych **`:::no-loc(class):::`** **`:::no-loc(struct):::`** typu,, lub **`:::no-loc(union):::`** . Wskazuje obiekt, dla którego wywoływana jest funkcja członkowska. Statyczne funkcje członkowskie nie mają **`:::no-loc(this):::`** wskaźnika.

## <a name="syntax"></a>Składnia

```cpp
:::no-loc(this):::
:::no-loc(this):::->member-identifier
```

## <a name="remarks"></a>Uwagi

**`:::no-loc(this):::`** Wskaźnik obiektu nie jest częścią samego obiektu. Nie jest to odzwierciedlone w wyniku **`:::no-loc(sizeof):::`** instrukcji dla obiektu. Gdy niestatyczna funkcja członkowska jest wywoływana dla obiektu, kompilator przekazuje adres obiektu do funkcji jako argument ukryty. Na przykład następujące wywołanie funkcji:

```cpp
myDate.setMonth( 3 );
```

można interpretować jako:

```cpp
setMonth( &myDate, 3 );
```

Adres obiektu jest dostępny z poziomu funkcji składowej jako **`:::no-loc(this):::`** wskaźnika. Większość **`:::no-loc(this):::`** użycia wskaźnika jest niejawna. Jest to niezbędne, ale nie jest konieczne, aby użyć jawnego w **`:::no-loc(this):::`** przypadku odwoływania się do członków :::no-loc(class)::: . Na przykład:

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   :::no-loc(this):::->month = mn;      // are equivalent
   (*:::no-loc(this):::).month = mn;
}
```

Wyrażenie **`*:::no-loc(this):::`** jest często używane do zwracania bieżącego obiektu z funkcji składowej:

```cpp
return *:::no-loc(this):::;
```

**`:::no-loc(this):::`** Wskaźnik jest również używany do ochrony przed odwołaniem do samego siebie:

```cpp
if (&Object != :::no-loc(this):::) {
// do not execute in cases of self-reference
```

> [!NOTE]
> Ponieważ **`:::no-loc(this):::`** wskaźnik nie jest modyfikowany, przypisania do **`:::no-loc(this):::`** wskaźnika są niedozwolone. Starsze implementacje języka C++ dozwolone przypisanie do **`:::no-loc(this):::`** .

Czasami **`:::no-loc(this):::`** wskaźnik jest używany bezpośrednio — na przykład w celu manipulowania danymi :::no-loc(struct)::: URES, gdzie wymagany jest adres bieżącego obiektu.

## <a name="example"></a>Przykład

```cpp
// :::no-loc(this):::_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

:::no-loc(class)::: Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( :::no-loc(const)::: Buf & );
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

Buf& Buf::operator=( :::no-loc(const)::: Buf &otherbuf )
{
    if( &otherbuf != :::no-loc(this)::: )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *:::no-loc(this):::;
}

int main()
{
    Buf myBuf( "my buffer", 10 );
    Buf yourBuf( "your buffer", 12 );

    // Display 'my buffer'
    myBuf.Display();

    // assignment operator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-no-locthis-pointer"></a>Typ :::no-loc(this)::: wskaźnika

**`:::no-loc(this):::`** Typ wskaźnika można zmodyfikować w deklaracji funkcji za pomocą **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** słów kluczowych i. Aby zadeklarować funkcję, która ma jeden z tych atrybutów, należy dodać słowa kluczowe po liście argumentów funkcji.

Rozważmy przykład:

```cpp
// type_of_:::no-loc(this):::_pointer1.cpp
:::no-loc(class)::: Point
{
    unsigned X() :::no-loc(const):::;
};
int main()
{
}
```

Poprzedni kod deklaruje funkcję członkowską, `X` , w której **`:::no-loc(this):::`** wskaźnik jest traktowany jako **`:::no-loc(const):::`** wskaźnik do **`:::no-loc(const):::`** obiektu. Można używać kombinacji opcji *OKS-mod-list* , ale zawsze modyfikują obiekt wskazywany przez **`:::no-loc(this):::`** wskaźnik, a nie sam wskaźnik. Poniższa deklaracja deklaruje funkcję `X` , gdzie **`:::no-loc(this):::`** wskaźnik jest **`:::no-loc(const):::`** wskaźnikiem do **`:::no-loc(const):::`** obiektu:

```cpp
// type_of_:::no-loc(this):::_pointer2.cpp
:::no-loc(class)::: Point
{
    unsigned X() :::no-loc(const):::;
};
int main()
{
}
```

Typ elementu **`:::no-loc(this):::`** w funkcji członkowskiej jest opisywany przez następującą składnię. *Lista kwalifikatorów CV* jest określana na podstawie deklarator funkcji składowej. Może być **`:::no-loc(const):::`** lub **`:::no-loc(volatile):::`** (lub obie). * :::no-loc(class)::: -Type* jest nazwą :::no-loc(class)::: :

[*CV-kwalifikator-list*] * :::no-loc(class)::: -Typ* ** \* :::no-loc(const)::: :::no-loc(this)::: **

Innymi słowy, **`:::no-loc(this):::`** wskaźnik jest zawsze :::no-loc(const)::: wskaźnikiem. Nie można go ponownie przypisać.  Kwalifikatory, które są **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** używane w deklaracji funkcji składowej, mają zastosowanie do wystąpienia, w którym :::no-loc(class)::: **`:::no-loc(this):::`** wskaźnik wskazuje, w zakresie tej funkcji.

W poniższej tabeli opisano więcej informacji o tym, jak działają te modyfikatory.

### <a name="semantics-of-no-locthis-modifiers"></a>Semantyka :::no-loc(this)::: modyfikatorów

|Modyfikator|Znaczenie|
|--------------|-------------|
|**`:::no-loc(const):::`**|Nie można zmienić danych elementu członkowskiego; nie można wywołać funkcji Członkowskich, które nie są **`:::no-loc(const):::`** .|
|**`:::no-loc(volatile):::`**|Dane elementu członkowskiego są ładowane z pamięci za każdym razem, gdy są dostępne; wyłącza pewne optymalizacje.|

Wystąpił błąd podczas przekazywania **`:::no-loc(const):::`** obiektu do funkcji członkowskiej, która nie jest **`:::no-loc(const):::`** .

Podobnie jest również błąd przekazywania **`:::no-loc(volatile):::`** obiektu do funkcji członkowskiej, która nie jest **`:::no-loc(volatile):::`** .

Funkcje składowe zadeklarowane jako **`:::no-loc(const):::`** nie mogą zmieniać danych elementu członkowskiego — w takich funkcjach **`:::no-loc(this):::`** wskaźnik jest wskaźnikiem do **`:::no-loc(const):::`** obiektu.

> [!NOTE]
> :::no-loc(struct):::Nie można zadeklarować con ORS i de :::no-loc(struct)::: ORS jako **`:::no-loc(const):::`** lub **`:::no-loc(volatile):::`** . Mogą jednak być wywoływane dla **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** obiektów lub.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)
