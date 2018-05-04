---
title: Wskaźniki do elementów członkowskich | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6312186ec47014ff11e18450543d8f98178a776b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="pointers-to-members"></a>Wskaźniki do elementów członkowskich
Deklaracje wskaźników do elementów członkowskich są specjalne przypadki deklaracje wskaźników.  Są deklarowane za pomocą następującej sekwencji:  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [ms-modifier]qualified-name ::* [cv-qualifiers] identifier  
[= & qualified-name :: member-name];  
```  
  
1.  Specyfikator deklaracji:  
  
    -   Specyfikator klasy magazynu opcjonalne.  
  
    -   Opcjonalne **const** i/lub `volatile` specyfikatory.  
  
    -   Specyfikator typu: Nazwa typu.  Jest to typ elementu członkowskiego, aby wskazywał, nie klasy.  
  
2.  Deklarator:  
  
    -   Opcjonalne Microsoft określonych modyfikatora. Aby uzyskać więcej informacji, zobacz [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
    -   Kwalifikowana nazwa klasy zawierającej elementy członkowskie, które można wskazywał.   
  
    -   :: — Operator.  
  
    -   **\*** Operatora.  
  
    -   Opcjonalne **const** i/lub `volatile` specyfikatory.  
  
    -   Identyfikator nazewnictwa wskaźnik do elementu członkowskiego.  
  
    -   Inicjator opcjonalne:  
  
 **=** Operatora.  
  
 **&** Operatora.  
  
 Kwalifikowana nazwa klasy.  
  
 Operator `::`.  
  
 Nazwa niestatycznego elementu członkowskiego klasy odpowiedniego typu.  
  
 Jak zawsze wiele deklaratorów (i wszystkie skojarzone inicjatory) są dozwolone w jednej deklaracji.  
  
 Wskaźnik do elementu członkowskiego klasy różni się od normalny wskaźnik, ponieważ zawiera ona informacje o typie dla typu elementu członkowskiego i klasy, do której należy element członkowski. Identyfikuje normalny wskaźnik (ma adres) pojedynczego obiektu w pamięci. Wskaźnik do elementu członkowskiego klasy identyfikuje ten element członkowski w żadnym wystąpieniu klasy. Poniższy przykład deklaruje klasy `Window`, a niektóre wskaźników do elementu członkowskiego danych.  
  
```  
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
  
 W powyższym przykładzie `pwCaption` wskaźnik do dowolnego elementu członkowskiego klasy `Window` mający typ **char\***. Typ `pwCaption` jest `char * Window::*`. Fragment kodu w następnym deklaruje wskaźniki do `SetCaption` i `GetCaption` funkcji elementów członkowskich.  
  
```  
const char * (Window::*pfnwGC)() = &Window::GetCaption;  
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;  
```  
  
 Wskaźniki `pfnwGC` i `pfnwSC` wskaż `GetCaption` i `SetCaption` z `Window` odpowiednio class. Kod kopiuje informacje tytuł okna bezpośrednio przy użyciu wskaźnika do elementu członkowskiego `pwCaption`:  
  
```  
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
  
 Różnica między **.\***  i **-> \*** operatory (operatory wskaźników do elementów członkowskich) oznacza, że **.\***  operator wybiera członków danego obiektu lub odwołanie do obiektu, podczas gdy **-> \*** operator wybiera elementów członkowskich za pomocą wskaźnika. (Aby uzyskać więcej informacji o tych operatorów, zobacz [wyrażenia z operatorami wskaźnika do elementu członkowskiego](../cpp/pointer-to-member-operators-dot-star-and-star.md).)  
  
 Wynik operatory wskaźników do elementów członkowskich jest typem elementu członkowskiego — w takim przypadku **char \*** .  
  
 Poniższy fragment kodu wywołuje funkcje Członkowskie `GetCaption` i `SetCaption` przy użyciu wskaźników do elementów członkowskich:  
  
```  
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
 Adres statyczny element członkowski nie jest wskaźnikiem do elementu członkowskiego. Jest to zwykły wskaźnik do pojedynczego wystąpienia statycznego elementu członkowskiego. Ponieważ istnieje tylko jedno wystąpienie statycznego elementu członkowskiego dla wszystkich obiektów klasy danego zwykłej address-of **(&)** i wyłuskania **(\*)** można używać operatorów.  
  
## <a name="pointers-to-members-and-virtual-functions"></a>Wskaźniki do elementów członkowskich i funkcji wirtualnych  
 Wywoływanie funkcji wirtualnej za pomocą funkcji wskaźnika do elementu członkowskiego działa tak, jakby funkcji ma została wywołana bezpośrednio; odpowiedniej funkcji jest wyszukiwana w tabeli v i wywoływane.  
  
 Klucz do funkcji wirtualnych, praca, jak zawsze wywołuje je za pomocą wskaźnika do klasy podstawowej. (Aby uzyskać więcej informacji na temat funkcji wirtualnych, zobacz [funkcji wirtualnych](../cpp/virtual-functions.md).)  
  
 Poniższy kod przedstawia sposób wywołania funkcji wirtualnej za pomocą funkcji wskaźników do elementów członkowskich:  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 