---
title: Zagnieżdżone deklaracje klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], declaring
- declarations, class
- nested classes [C++]
- nested classes [C++], declaring
- declaring classes [C++]
- declarations, nested classes
ms.assetid: c02e471d-b7f9-41b8-8ef6-2323f006dbd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 870245fa8a13ac4950a7940fcb4738bd1f50ebe1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087737"
---
# <a name="nested-class-declarations"></a>Zagnieżdżone deklaracje klas

Klasa może być zadeklarowana w zakresie innej klasy. Taka klasa nosi nazwę „klasy zagnieżdżonej”. Klasy zagnieżdżone są rozważane w zakresie otaczającej klasy i są dostępne do użycia w tym zakresie. Aby odwołać się do klasy zagnieżdżonej z zakresu innego niż jego bezpośredni zasięg, należy użyć w pełni kwalifikowanej nazwy.

Poniższy przykład pokazuje sposób deklarowania klas zagnieżdżonych:

```cpp
// nested_class_declarations.cpp
class BufferedIO
{
public:
   enum IOError { None, Access, General };

   // Declare nested class BufferedInput.
   class BufferedInput
   {
   public:
      int read();
      int good()
      {
         return _inputerror == None;
      }
   private:
       IOError _inputerror;
   };

   // Declare nested class BufferedOutput.
   class BufferedOutput
   {
      // Member list
   };
};

int main()
{
}
```

`BufferedIO::BufferedInput` i `BufferedIO::BufferedOutput` są zadeklarowane w ramach `BufferedIO`. Nazwy klas nie są widoczne w zakresie klasy `BufferedIO`. Jednak obiekt typu `BufferedIO` nie zawiera żadnych obiektów typu `BufferedInput` lub `BufferedOutput`.

Klasy zagnieżdżone mogą bezpośrednio korzystać z nazw, nazwy typów, nazw statycznych składowych i wyliczeń tylko z otaczającej klasy. Aby używać nazw innych składowych klasy, należy użyć wskaźników, odwołań lub nazw obiektów.

W poprzednim przykładzie `BufferedIO`, wyliczenie `IOError` jest dostępne bezpośrednio przez funkcje składowe w klasach zagnieżdżonych `BufferedIO::BufferedInput` lub `BufferedIO::BufferedOutput`, jak pokazano w funkcji `good`.

> [!NOTE]
>  Klasy zagnieżdżone deklarują tylko typy w zakresie klasy. Nie przyczyniają się do tworzenia obiektów, w których zagnieżdżone są klasy. Poprzedni przykład deklaruje dwie klasy zagnieżdżone, ale nie deklaruje żadnych obiektów tego typu klas.

Wyjątkiem zakresu widoczności deklaracji klasy zagnieżdżonej jest nazwa typu zadeklarowana wraz z deklaracją do przodu.  W tym przypadku nazwa klasy zadeklarowanej deklaracji do przodu jest widoczna spoza otaczającej klasy z jej zakresem zdefiniowanym jako najmniejszy otaczający zakres.  Na przykład:

```cpp
// nested_class_declarations_2.cpp
class C
{
public:
    typedef class U u_t; // class U visible outside class C scope
    typedef class V {} v_t; // class V not visible outside class C
};

int main()
{
    // okay, forward declaration used above so file scope is used
    U* pu;

    // error, type name only exists in class C scope
    u_t* pu2; // C2065

    // error, class defined above so class C scope
    V* pv; // C2065

    // okay, fully qualified name
    C::V* pv2;
}
```

## <a name="access-privilege-in-nested-classes"></a>Uprawnienia dostępu w zagnieżdżonych klasach

Zagnieżdżanie klasy, w ramach innej klasy nie daje uprawnień dostępu do składowych klasy zagnieżdżonej. Podobnie funkcji elementów członkowskich otaczającej klasy nie mają specjalne dostępu do składowych klasy zagnieżdżone.

## <a name="member-functions-in-nested-classes"></a>Zaprzyjaźnione funkcje w zagnieżdżonych klasach

Funkcji elementów członkowskich zadeklarowanych w klasach zagnieżdżonych można zdefiniować w zakresie pliku. Poprzedni przykład może być napisane tak:

```cpp
// member_functions_in_nested_classes.cpp
class BufferedIO
{
public:
    enum IOError { None, Access, General };
    class BufferedInput
    {
    public:
        int read(); // Declare but do not define member
        int good(); //  functions read and good.
    private:
        IOError _inputerror;
    };

    class BufferedOutput
    {
        // Member list.
    };
};
// Define member functions read and good in
//  file scope.
int BufferedIO::BufferedInput::read()
{
   return(1);
}

int BufferedIO::BufferedInput::good()
{
    return _inputerror == None;
}
int main()
{
}
```

W powyższym przykładzie *kwalifikowana type-name* używana jest składnia do deklarowania nazwy funkcji. Deklaracji:

```cpp
BufferedIO::BufferedInput::read()
```

oznacza, że " `read` funkcja, która jest elementem członkowskim `BufferedInput` klasę, która znajduje się w zakresie `BufferedIO` klasy." Ponieważ ta deklaracja korzysta *kwalifikowana type-name* składni, możliwe są konstrukcje następującą postać:

```cpp
typedef BufferedIO::BufferedInput BIO_INPUT;

int BIO_INPUT::read()
```

Poprzednia deklaracja jest równoważna do poprzedniego, ale używa on **typedef** nazwę zamiast nazwy klas.

## <a name="friend-functions-in-nested-classes"></a>Zaprzyjaźnione funkcje w zagnieżdżonych klasach

Friend — funkcje zadeklarowane w klasie zagnieżdżonej są uznawane za w zakresie klasy zagnieżdżonej nie otaczającej klasy. Friend — funkcje uzyskać nie uprawnienia dostępu do członków ani funkcji elementów członkowskich otaczającej klasy. Jeśli chcesz użyć nazwy, która jest zadeklarowana w klasie zagnieżdżonej w funkcji zaprzyjaźnionej, funkcja zaprzyjaźniona jest zdefiniowana w zakresie pliku użyć kwalifikowanych nazw typów w następujący sposób:

```cpp
// friend_functions_and_nested_classes.cpp

#include <string.h>

enum
{
    sizeOfMessage = 255
};

char *rgszMessage[sizeOfMessage];

class BufferedIO
{
public:
    class BufferedInput
    {
    public:
        friend int GetExtendedErrorStatus();
        static char *message;
        static int  messageSize;
        int iMsgNo;
   };
};

char *BufferedIO::BufferedInput::message;
int BufferedIO::BufferedInput::messageSize;

int GetExtendedErrorStatus()
{
    int iMsgNo = 1; // assign arbitrary value as message number

    strcpy_s( BufferedIO::BufferedInput::message,
              BufferedIO::BufferedInput::messageSize,
              rgszMessage[iMsgNo] );

    return iMsgNo;
}

int main()
{
}
```

Poniższy kod przedstawia funkcję `GetExtendedErrorStatus` zadeklarowana jako funkcja zaprzyjaźniona. W funkcji, która jest zdefiniowana w zakresie pliku, komunikat jest kopiowana z tablicy statycznej do składowej klasy. Należy pamiętać, że lepszej realizacji `GetExtendedErrorStatus` jest Zadeklaruj go jako:

```cpp
int GetExtendedErrorStatus( char *message )
```

Poprzedni interfejs kilka klas może korzystać z usług tę funkcję, przekazując lokalizacji pamięci, gdzie mają być kopiowane komunikat o błędzie.

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)