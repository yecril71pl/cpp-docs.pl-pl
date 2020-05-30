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
ms.openlocfilehash: 75bd29310d64b0309ac48be053aa43cc0084aa2d
ms.sourcegitcommit: 1a8fac06478da8bee1f6d70e25afbad94144af1a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2020
ms.locfileid: "84226097"
---
# <a name="pointers-to-members"></a>Wskaźniki do elementów członkowskich

Deklaracje wskaźników do elementów członkowskich to specjalne przypadki deklaracji wskaźnika.  Są one deklarowane przy użyciu następującej sekwencji:

> *specyfikatory klasy magazynu*<sub>opt</sub> wybierają *kwalifikatory życiorysu*<sub>opt</sub> *Typ-specyfikatora* *MS-modyfikator*<sub>opt</sub> *kwalifikacji do* **`::*`** *kwalifikatora CV*<sub>opt</sub> *identifier* *pm-initializer*<sub>opt</sub>**`;`**

1. Specyfikator deklaracji:

   - Opcjonalny specyfikator klasy magazynu.

   - Opcjonalne specyfikatory **const** i **volatile** .

   - Specyfikator typu: nazwa typu. Jest to typ elementu członkowskiego, który ma być wskazywany, a nie Klasa.

1. Deklarator:

   - Opcjonalny modyfikator specyficzny dla firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md).

   - Kwalifikowana nazwa klasy zawierającej członków do wskazywania.

   - __`::`__ Operator.

   - __`*`__ Operator.

   - Opcjonalne specyfikatory **const** i **volatile** .

   - Identyfikator identyfikujący wskaźnik do elementu członkowskiego.

1. Opcjonalny inicjator wskaźnika do składowej:

   - **`=`** Operator.

   - **`&`** Operator.

   - Kwalifikowana nazwa klasy.

   - __`::`__ Operator.

   - Nazwa niestatycznej składowej klasy odpowiedniego typu.

Jak zawsze, wiele Deklaratory (i skojarzonych inicjatorów) są dozwolone w jednej deklaracji. Wskaźnik do elementu członkowskiego nie może wskazywać statycznej składowej klasy, składowej typu referencyjnego lub **`void`** .

Wskaźnik do składowej klasy różni się od normalnego wskaźnika: zawiera informacje o typie elementu członkowskiego i dla klasy, do której należy element członkowski. Normalny wskaźnik identyfikuje (ma adres) tylko jeden obiekt w pamięci. Wskaźnik do składowej klasy identyfikuje ten element członkowski w dowolnym wystąpieniu klasy. Poniższy przykład deklaruje klasę, `Window` i niektóre wskaźniki do danych elementu członkowskiego.

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       // Window size.
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

W poprzednim przykładzie, `pwCaption` jest wskaźnikiem do dowolnego elementu członkowskiego klasy `Window` , która jest typu `char*` . Typ `pwCaption` to `char * Window::*` . Następny fragment kodu deklaruje wskaźniki do `SetCaption` `GetCaption` funkcji składowych i.

```cpp
const char * (Window::* pfnwGC)() = &Window::GetCaption;
bool (Window::* pfnwSC)( const char * ) = &Window::SetCaption;
```

Odpowiednio wskaźniki `pfnwGC` i `pfnwSC` punkty do `GetCaption` i `SetCaption` z `Window` klasy. Kod kopiuje informacje do podpisu okna bezpośrednio przy użyciu wskaźnika do elementu członkowskiego `pwCaption` :

```cpp
Window  wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int     cUntitledLen  = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     // same as
// wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; // same as
// pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

Różnica między **`.*`** **`->*`** operatorami i (operatorami wskaźnik-do-składowej) polega na tym, że **`.*`** operator wybiera elementy członkowskie z odwołaniem do obiektu lub obiektu, podczas gdy **`->*`** operator wybiera członków za pomocą wskaźnika. Aby uzyskać więcej informacji na temat tych operatorów, zobacz [wyrażenia z operatorami wskaźnika do składowej](../cpp/pointer-to-member-operators-dot-star-and-star.md).

Wynik operatorów wskaźnika do składowej jest typem elementu członkowskiego. W tym przypadku jest to `char *` .

Poniższy fragment kodu wywołuje funkcje członkowskie `GetCaption` i `SetCaption` używa wskaźników do elementów członkowskich:

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

Adres statycznego elementu członkowskiego nie jest wskaźnikiem do elementu członkowskiego. Jest to zwykły wskaźnik do jednego wystąpienia statycznego elementu członkowskiego. Dla wszystkich obiektów danej klasy istnieje tylko jedno wystąpienie statycznej składowej. Oznacza to, że można używać zwykłych operatorów address-of ( **&** ) i unreference ( <strong>\*</strong> ).

## <a name="pointers-to-members-and-virtual-functions"></a>Wskaźniki do elementów członkowskich i funkcji wirtualnych

Wywoływanie funkcji wirtualnej za pomocą funkcji wskaźnika do składowej działa tak, jakby funkcja została wywołana bezpośrednio. Poprawna funkcja jest wyszukiwana w tabeli v i wywoływana.

Klucz do działających funkcji wirtualnych, tak jak zawsze, jest wywoływany przez wskaźnik do klasy bazowej. (Aby uzyskać więcej informacji na temat funkcji wirtualnych, zobacz [funkcje wirtualne](../cpp/virtual-functions.md)).

Poniższy kod przedstawia sposób wywołania funkcji wirtualnej za pomocą funkcji wskaźnika do składowej:

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
void (Base::* bfnPrint)() = &Base::Print;
void Base::Print()
{
    cout << "Print function for class Base" << endl;
}

class Derived : public Base
{
public:
    void Print();  // Print is still a virtual function.
};

void Derived::Print()
{
    cout << "Print function for class Derived" << endl;
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

// Output:
// Print function for class Base
// Print function for class Derived
```
