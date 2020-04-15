---
title: Wskaźniki do elementów członkowskich
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
ms.openlocfilehash: adffacc3ddc08679d7db4e17e027d8a7dbe8a92b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320318"
---
# <a name="pointers-to-members"></a>Wskaźniki do elementów członkowskich

Deklaracje wskaźników do elementów członkowskich są szczególnymi przypadkami deklaracji wskaźnika.  Są one deklarowane przy użyciu następującej sekwencji:

> *storage-class-specifiers*<sub>opt</sub> *cv-qualifiers*<sub>opt</sub> *type-specifier* *ms-modifier*<sub>opt</sub> *qualified-name* **`::*`** *cv-qualifiers*<sub>opt</sub> *identifier* *pm-initializer*<sub>opt</sub>**`;`**

1. Specyfikator deklaracji:

   - Opcjonalny specyfikator klasy magazynu.

   - Opcjonalne **specyfikatory const** i **volatile.**

   - Specyfikator typu: nazwa typu. Jest to typ członka, który należy wskazać, a nie klasa.

1. Zgłaszający:

   - Opcjonalny modyfikator specyficzny dla firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md).

   - Kwalifikowana nazwa klasy zawierającej elementy członkowskie, na które należy wskazać.

   - Operator. __`::`__

   - Operator. __`*`__

   - Opcjonalne **specyfikatory const** i **volatile.**

   - Identyfikator nazewnictwa wskaźnika do elementu członkowskiego.

1. Opcjonalny inicjator wskaźnika do elementu:

   - Operator. **`=`**

   - Operator. **`&`**

   - Kwalifikowana nazwa klasy.

   - Operator. __`::`__

   - Nazwa niestatycznego elementu członkowskiego klasy odpowiedniego typu.

Jak zawsze wiele deklaratorów (i wszelkie skojarzone inicjatory) są dozwolone w jednej deklaracji. Wskaźnik do elementu członkowskiego nie może wskazywać statycznego elementu członkowskiego klasy, **`void`** elementu członkowskiego typu odwołania lub .

Wskaźnik do elementu członkowskiego klasy różni się od normalnego wskaźnika: zawiera zarówno informacje o typie dla typu elementu członkowskiego, jak i dla klasy, do której należy element członkowski. Normalny wskaźnik identyfikuje (ma adres) tylko jeden obiekt w pamięci. Wskaźnik do członka klasy identyfikuje tego elementu członkowskiego w dowolnym wystąpieniu klasy. Poniższy przykład deklaruje klasę, `Window`a niektóre wskaźniki do danych członkowskich.

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

W poprzednim przykładzie `pwCaption` jest wskaźnikiem do `Window` dowolnego członka klasy, który jest typem `char*`. Typ jest `pwCaption` `char * Window::*`. Następny fragment kodu deklaruje wskaźniki `SetCaption` do `GetCaption` funkcji i elementów członkowskich.

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

Wskaźniki `pfnwGC` `pfnwSC` i wskazać `GetCaption` do `SetCaption` i `Window` klasy, odpowiednio. Kod kopiuje informacje do podpisu okna bezpośrednio `pwCaption`za pomocą wskaźnika do elementu członkowskiego:

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

Różnica między **`.*`** operatorami i **`->*`** operatorów (operatory wskaźnik **`.*`** do elementu członkowskiego) jest to, że **`->*`** operator wybiera elementy członkowskie podane obiektu lub obiektu odniesienia, podczas gdy operator wybiera elementy członkowskie za pomocą wskaźnika. Aby uzyskać więcej informacji na temat tych operatorów, zobacz [wyrażenia z operatorami wskaźnik-element członkowski](../cpp/pointer-to-member-operators-dot-star-and-star.md).

Wynikiem operatorów wskaźnik-element jest typ elementu członkowskiego. W tym przypadku jest `char *`to .

Następujący fragment kodu wywołuje `GetCaption` funkcje `SetCaption` elementu członkowskiego i przy użyciu wskaźników do elementów członkowskich:

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

Adres statycznego elementu członkowskiego nie jest wskaźnikiem do elementu członkowskiego. Jest to zwykły wskaźnik do jednego wystąpienia statycznego elementu członkowskiego. Tylko jedno wystąpienie statycznego elementu członkowskiego istnieje dla wszystkich obiektów danej klasy. Oznacza to, że można użyć**&** zwykłych operatorów<strong>\*</strong>adresu ( ) i wyłudu ( ) .

## <a name="pointers-to-members-and-virtual-functions"></a>Wskaźniki do elementów członkowskich i funkcji wirtualnych

Wywoływanie funkcji wirtualnej za pośrednictwem funkcji wskaźnik do elementu członkowskiego działa tak, jakby funkcja została wywołana bezpośrednio. Prawidłowa funkcja jest wyszukany w tabeli v i wywoływane.

Klucz do funkcji wirtualnych pracy, jak zawsze, jest wywoływanie ich za pośrednictwem wskaźnika do klasy podstawowej. (Aby uzyskać więcej informacji na temat funkcji wirtualnych, zobacz [Funkcje wirtualne](../cpp/virtual-functions.md).)

Poniższy kod pokazuje, jak wywołać funkcję wirtualną za pomocą funkcji wskaźnik do elementu członkowskiego:

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
