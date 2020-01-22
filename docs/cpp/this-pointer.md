---
title: this wskaźnik
description: this wskaźnik jest generowanym przez kompilator wskaźnikiem do bieżącego obiektu w niestatycznych funkcjach składowych.
ms.date: 01/22/2020
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- this
- class
- struct
- union
- sizeof
- const
- volatile
ms.openlocfilehash: 58bba2edd7a457c624b747b5a65d209995852848
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518338"
---
# <a name="opno-locthis-pointer"></a>this wskaźnik

Wskaźnik **this** jest dostępny tylko w obrębie niestatycznych funkcji składowych typu **class** , **struct** lub **union** . Wskazuje obiekt, dla którego wywoływana jest funkcja członkowska. Statyczne funkcje członkowskie nie mają wskaźnika **this** .

## <a name="syntax"></a>Składnia

```cpp
this
this->member-identifier
```

## <a name="remarks"></a>Uwagi

Wskaźnik **this** obiektu nie jest częścią samego obiektu. Nie jest to odzwierciedlone w wyniku instrukcji **sizeof** w obiekcie. Gdy niestatyczna funkcja członkowska jest wywoływana dla obiektu, kompilator przekazuje adres obiektu do funkcji jako argument ukryty. Na przykład następujące wywołanie funkcji:

```cpp
myDate.setMonth( 3 );
```

można interpretować jako:

```cpp
setMonth( &myDate, 3 );
```

Adres obiektu jest dostępny z poziomu funkcji składowej jako wskaźnika **this** . Większość **thisych** użycia wskaźników jest niejawna. W przypadku odwoływania się do członków classmożna używać jawnej **this** . Na przykład:

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   this->month = mn;      // are equivalent
   (*this).month = mn;
}
```

Wyrażenie `*this` jest często używane do zwracania bieżącego obiektu z funkcji składowej:

```cpp
return *this;
```

**this** wskaźnik jest również używany do ochrony przed odwołaniem do samego siebie:

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
> Ponieważ wskaźnik **this** nie jest modyfikowany, przypisania do wskaźnika **this** są niedozwolone. Starsze implementacje C++ dozwolonego przypisania do **this** .

Czasami wskaźnik **this** jest używany bezpośrednio — na przykład w celu manipulowania strukturami danych, w których jest wymagany adres bieżącego obiektu.

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

## <a name="type-of-the-opno-locthis-pointer"></a>Typ wskaźnika this

Typ wskaźnika **this** można modyfikować w deklaracji funkcji za pomocą słów kluczowych **const** i **volatile** . Aby zadeklarować funkcję, która ma jeden z tych atrybutów, należy dodać słowa kluczowe po liście argumentów funkcji.

Rozważmy przykład:

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

Poprzedni kod deklaruje funkcję elementu członkowskiego, `X`, w której wskaźnik **this** jest traktowany jako wskaźnik **const** do obiektu **const** . Można używać kombinacji opcji *OKS-mod-list* , ale zawsze modyfikuje obiekt wskazywany przez wskaźnik **this** , a nie sam wskaźnik. Poniższa deklaracja deklaruje funkcję `X`, gdzie wskaźnik **this** jest **constm** wskaźnikiem do obiektu **const** :

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

Typ **this** w funkcji składowej jest opisywany przez następującą składnię. *Lista kwalifikatorów CV* jest określana na podstawie deklarator funkcji składowej. Może być **const** lub **volatile** (lub oba te elementy). *class-Type* jest nazwą class:

[*CV-kwalifikator-list*] *classtypu* **\* const this**

Innymi słowy, **this** wskaźnik jest zawsze const wskaźnikiem. Nie można go ponownie przypisać.  Kwalifikatory **const** lub **volatile** używane w deklaracji funkcji składowej stosują się do class wystąpienia **this** wskaźnik wskazuje w, w zakresie tej funkcji.

W poniższej tabeli opisano więcej informacji o tym, jak działają te modyfikatory.

### <a name="semantics-of-opno-locthis-modifiers"></a>Semantyka this modyfikatorów

|Modyfikator|Znaczenie|
|--------------|-------------|
|**const**|Nie można zmienić danych elementu członkowskiego; nie można wywołać funkcji Członkowskich, które nie są **const** .|
|**volatile**|Dane elementu członkowskiego są ładowane z pamięci za każdym razem, gdy są dostępne; wyłącza pewne optymalizacje.|

Wystąpił błąd podczas przekazywania obiektu **const** do funkcji członkowskiej, która nie jest **const** .

Podobnie jest również błąd przekazywania obiektu **volatile** do funkcji członkowskiej, która nie jest **volatile** .

Funkcje składowe zadeklarowane jako **const** nie mogą zmieniać danych elementu członkowskiego — w takich funkcjach wskaźnik **this** jest wskaźnikiem do obiektu **const** .

> [!NOTE]
> Konstruktory i destruktory nie mogą być deklarowane jako **const** ani **volatile** . Mogą jednak być wywoływane dla obiektów **const** lub **volatile** .

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)
