---
title: Wskaźniki do składowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 509181abc0d9b3e2f2c2d4c76275e635ba3a4477
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076076"
---
# <a name="pointers-to-members"></a>Wskaźniki do elementów członkowskich

Deklaracje wskaźników do elementów członkowskich są specjalne przypadki deklaracje wskaźników.  Są deklarowane za pomocą następującej sekwencji:

```
[storage-class-specifiers] [cv-qualifiers] type-specifiers [ms-modifier]qualified-name ::* [cv-qualifiers] identifier
[= & qualified-name :: member-name];
```

1. Specyfikator deklaracji:
  - Specyfikator klasy magazynowania opcjonalne.

  - Opcjonalnie **const** i/lub **volatile** specyfikatorów.

  - Specyfikator typu: Nazwa typu.  Jest to typ elementu członkowskiego, aby wskazywał, nie klasy.

1. Specyfikator:

  - Opcjonalny modyfikator właściwy dla Microsoft. Aby uzyskać więcej informacji, zobacz [Modyfikatory specyficzne dla Microsoft](../cpp/microsoft-specific-modifiers.md).
1. Kwalifikowana nazwa klasy zawierającej członków do będzie wskazywał na.
  - :: Operator.
  - <strong>\*</strong> Operatora.
  - Opcjonalnie **const** i/lub **volatile** specyfikatorów.
  - Identyfikator nazwy wskaźnika do składowej.

  - Opcjonalny inicjator:
  - **=** Operatora.
  - **&** Operatora.
  - Kwalifikowana nazwa klasy.
  - Operator `::`.
  - Nazwa niestatycznej składowej klasy odpowiedniego typu.
  -  Jak zawsze wiele deklaratorów (i wszystkie skojarzone inicjatory) są dozwolone w jednej deklaracji.

Wskaźnik do składowej klasy typu różni się od normalnych wskaźnika, ponieważ zawiera ona informacje o typie dla typu elementu członkowskiego i klasy, do której należy dany element członkowski. Identyfikuje normalny wskaźnik (ma adres) pojedynczego obiektu w pamięci. Wskaźnik do składowej klasy identyfikuje ten element członkowski w żadnym wystąpieniu klasy. Poniższy przykład deklaruje klasę, `Window`i niektóre wskaźników do danych elementów członkowskich.

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       //  window size.
bool SetCaption( const char *szTitle ); // Set window caption.
   const char *GetCaption();               // Get window caption.
   char *szWinCaption;                     // Window caption.
};

// Declare a pointer to the data member szWinCaption.
char * Window::* pwCaption = &Window::szWinCaption;
int main()
{
}
```

W powyższym przykładzie `pwCaption` jest wskaźnikiem do wszystkich elementów członkowskich klasy `Window` zawierający typ `char*`. Typ `pwCaption` jest `char * Window::* `. Następny fragment kodu deklaruje wskaźniki do `SetCaption` i `GetCaption` funkcji elementów członkowskich.

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

Wskaźniki `pfnwGC` i `pfnwSC` wskaż `GetCaption` i `SetCaption` z `Window` klasy, odpowiednio. Kod kopiuje informacje tytuł okna bezpośrednio za pomocą wskaźnika do składowej `pwCaption`:

```cpp
Window wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int    cUntitledLen   = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     //same as
//wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; //same as //pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

Różnica między **.** <strong>\*</strong> i **->** <strong>\*</strong> operatorów (operatory wskaźników do elementów członkowskich) jest to, że **.** <strong>\*</strong> operator wybiera elementy członkowskie danego obiektu lub odwołanie do obiektu, podczas gdy **->** <strong>\*</strong> — operator wybiera elementy członkowskie za pomocą wskaźnika. (Aby uzyskać więcej informacji o tych operatorów, zobacz [wyrażenia zawierające operatory wskaźników do elementów członkowskich](../cpp/pointer-to-member-operators-dot-star-and-star.md).)

Wynik operatory wskaźników do elementów członkowskich jest typ elementu członkowskiego — w tym przypadku `char *`.

Poniższy fragment kodu wywołuje funkcje elementów członkowskich `GetCaption` i `SetCaption` za pomocą wskaźników do elementów członkowskich:

```cpp
// Allocate a buffer.
enum {
    sizeOfBuffer = 100
};
char szCaptionBase[sizeOfBuffer];

// Copy the main window caption into the buffer
//  and append " [View 1]".
strcpy_s( szCaptionBase, sizeOfBuffer, (wMainWindow.*pfnwGC)() );
strcat_s( szCaptionBase, sizeOfBuffer, " [View 1]" );
// Set the child window's caption.
(pwChildWindow->*pfnwSC)( szCaptionBase );
```

## <a name="restrictions-on-pointers-to-members"></a>Ograniczenia dotyczące wskaźników do elementów członkowskich

Adres statyczny element członkowski nie jest wskaźnik do elementu członkowskiego. Jest to zwykły wskaźnik do jednego wystąpienia statycznego elementu członkowskiego. Ponieważ istnieje tylko jedno wystąpienie statyczny element członkowski, dla wszystkich obiektów klasy danego zwykłych address-of (**&**) i wyłuskania (<strong>\*</strong>) można używać operatorów.

## <a name="pointers-to-members-and-virtual-functions"></a>Wskaźniki do elementów członkowskich i funkcji wirtualnych

Wywoływanie funkcji wirtualnej za pomocą funkcji wskaźnika do składowej działa tak, jakby funkcja jakby została ona bezpośrednio wywołana; poprawnej funkcji są wyszukiwane w tabeli v i wywołana.

Klucz do funkcji wirtualnych działa, jak zawsze wywołuje je za pomocą wskaźnika do klasy bazowej. (Aby uzyskać więcej informacji na temat funkcji wirtualnych, zobacz [funkcji wirtualnych](../cpp/virtual-functions.md).)

Poniższy kod przedstawia sposób wywołania funkcji wirtualnej za pomocą funkcji wskaźnika do elementu członkowskiego:

```cpp
// virtual_functions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base
{
    public:
    virtual void Print();
};
void (Base ::* bfnPrint)() = &Base :: Print;
void Base :: Print()
{
    cout << "Print function for class Base\n";
}

class Derived : public Base
{
    public:
    void Print();  // Print is still a virtual function.
};

void Derived :: Print()
{
    cout << "Print function for class Derived\n";
}

int main()
{
    Base   *bPtr;
    Base    bObject;
    Derived dObject;
    bPtr = &bObject;    // Set pointer to address of bObject.
    (bPtr->*bfnPrint)();
    bPtr = &dObject;    // Set pointer to address of dObject.
    (bPtr->*bfnPrint)();
}

//Output: Print function for class Base
Print function for class Derived
```