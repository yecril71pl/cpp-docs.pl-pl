---
title: Pojedyncze dziedziczenie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- single inheritance
- base classes [C++], indirect
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- derived classes [C++], single base class
- inheritance, single
ms.assetid: 1cb946ed-8b1b-4cf1-bde0-d9cecbfdc622
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c896b9ae68aad6e537655f03585f2261203099e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="single-inheritance"></a>Pojedyncze dziedziczenie
W "pojedyncze dziedziczenie," wspólnej formy dziedziczenia klasy mają tylko jedną klasę podstawową. Należy wziąć pod uwagę relację przedstawiono na poniższej ilustracji.  
  
 ![Jednym z podstawowych &#45; Wykres dziedziczenia](../cpp/media/vc38xj1.gif "vc38XJ1")  
Prosty wykres dziedziczące pojedynczo  
  
 Należy pamiętać, przejście z ogólne do określonych na rysunku. Znaleziono w projekcie większość klasy hierarchie innego atrybutu wspólnego jest klasy pochodnej z klasy podstawowej "rodzaju" relacją. Na rysunku `Book` jest rodzajem elementu `PrintedDocument`i `PaperbackBook` jest rodzajem elementu `book`.  
  
 Jeden element z uwagi na rysunku: `Book` jest zarówno klasy pochodnej (z `PrintedDocument`) i klasę podstawową (`PaperbackBook` jest pochodną `Book`). W poniższym przykładzie pokazano deklaracji szkieletowych hierarchii klas:  
  
```  
// deriv_SingleInheritance.cpp  
// compile with: /LD  
class PrintedDocument {};  
  
// Book is derived from PrintedDocument.  
class Book : public PrintedDocument {};  
  
// PaperbackBook is derived from Book.  
class PaperbackBook : public Book {};  
```  
  
 `PrintedDocument`uważa się klasy "bezpośredniej klasy podstawowej" `Book`; jest to klasa "base pośredniego" do `PaperbackBook`. Różnica polega na tym że bezpośredniej klasie podstawowej pojawi się na liście podstawowej deklaracji klasy, a nie jest pośrednie base.  
  
 Klasa podstawowa, z którego pochodzi każdej klasy jest zadeklarowana przed deklaracją klasy pochodnej. Nie jest wystarczające, aby zapewnić deklaracji odwołujące się do przodu dla klasy podstawowej; musi istnieć pełne deklaracji.  
  
 W powyższym przykładzie specyfikator dostępu **publicznego** jest używany. Znaczenie publicznych, chronionych i prywatnych dziedziczenia jest opisana w [kontroli dostępu do elementu członkowskiego.](../cpp/member-access-control-cpp.md)  
  
 Klasa może służyć jako klasę podstawową dla wielu określonej klasy, jak pokazano na poniższej ilustracji.  
  
 ![Ukierunkowanego wykresu acyklicznego](../cpp/media/vc38xj2.gif "vc38XJ2")  
Przykładowe ukierunkowanego wykresu acyklicznego.  
  
 Na diagramie pokazano powyżej o nazwie "ukierunkowanego wykresu acyklicznego" (lub "DAG"), niektórych klas są klasy podstawowej dla więcej niż jednej klasy pochodnej. Jednak odwrotnej nie jest prawdziwe: istnieje tylko jeden bezpośrednia klasa podstawowa dla żadnej podanej pochodnej klasy. Wykres na ilustracji przedstawiono struktury "pojedyncze dziedziczenie".  
  
> [!NOTE]
>  Ukierunkowanego wykresu acyklicznego. nie są unikatowe dla pojedynczego dziedziczenia. Są one również używane do przedstawiać wykresy dziedziczenia wielokrotnego. W tym temacie omówiono [dziedziczenie wielokrotne](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca).  
  
 W dziedziczeniu Klasa pochodna zawiera elementy członkowskie klasy podstawowej oraz nowych elementów członkowskich, które można dodać. W związku z tym Klasa pochodna może odwoływać się do elementów członkowskich klasy podstawowej, (chyba że te elementy członkowskie są ponownie zdefiniowana w klasie pochodnej). Operator rozpoznawania zakresu (`::`) można odwołać się do elementów członkowskich bezpośredniej lub pośredniej klasy podstawowej, jeśli takie elementy mają został ponownie zdefiniować w klasie pochodnej. Rozważmy następujący przykład:  
  
```  
// deriv_SingleInheritance2.cpp  
// compile with: /EHsc /c  
#include <iostream>  
using namespace std;  
class Document {  
public:  
   char *Name;   // Document name.  
   void PrintNameOf();   // Print name.  
};  
  
// Implementation of PrintNameOf function from class Document.  
void Document::PrintNameOf() {  
   cout << Name << endl;  
}  
  
class Book : public Document {  
public:  
   Book( char *name, long pagecount );  
private:  
   long  PageCount;  
};  
  
// Constructor from class Book.  
Book::Book( char *name, long pagecount ) {  
   Name = new char[ strlen( name ) + 1 ];  
   strcpy_s( Name, strlen(Name), name );  
   PageCount = pagecount;  
};  
```  
  
 Należy pamiętać, że Konstruktor `Book`, (`Book::Book`), ma dostęp do elementu członkowskiego danych, `Name`. W programie, typu obiektu `Book` można tworzyć i używane w następujący sposób:  
  
```  
//  Create a new object of type Book. This invokes the  
//   constructor Book::Book.  
Book LibraryBook( "Programming Windows, 2nd Ed", 944 );  
  
...  
  
//  Use PrintNameOf function inherited from class Document.  
LibraryBook.PrintNameOf();  
```  
  
 W poprzednim przykładzie pokazano, element członkowski klasy i dziedziczone dane i funkcje używane są identyczne. Jeśli Implementacja klasy `Book` wymaga ponowna implementacja elementu `PrintNameOf` funkcji, funkcji, który należy do `Document` klasa może zostać wywołana tylko przy użyciu rozpoznawania zakresu (`::`) — operator:  
  
```  
// deriv_SingleInheritance3.cpp  
// compile with: /EHsc /LD  
#include <iostream>  
using namespace std;  
  
class Document {  
public:  
   char *Name;          // Document name.  
   void  PrintNameOf() {}  // Print name.  
};  
  
class Book : public Document {  
   Book( char *name, long pagecount );  
   void PrintNameOf();  
   long  PageCount;  
};  
  
void Book::PrintNameOf() {  
   cout << "Name of book: ";  
   Document::PrintNameOf();  
}  
```  
  
 Wskaźniki i odwołań do klas pochodnych można niejawnie Jeśli można zamienić na wskaźniki i odwołania do ich klasami podstawowymi jest dostępny, jednoznaczne klasy podstawowej. Poniższy kod ilustruje tę koncepcję przy użyciu wskaźników (ta sama zasada dotyczy odwołania):  
  
```  
// deriv_SingleInheritance4.cpp  
// compile with: /W3  
struct Document {  
   char *Name;  
   void PrintNameOf() {}  
};  
  
class PaperbackBook : public Document {};  
  
int main() {  
   Document * DocLib[10];   // Library of ten documents.  
   for (int i = 0 ; i < 10 ; i++)  
      DocLib[i] = new Document;  
}  
```  
  
 W powyższym przykładzie są tworzone różne typy. Jednak ponieważ te typy są pochodzące z `Document` klasy, istnieje niejawna konwersja na `Document *`. W związku z tym `DocLib` jest "Lista heterogenicznych" (w którym nie wszystkie obiekty są tego samego typu list) zawierający różnymi rodzajami obiektów.  
  
 Ponieważ `Document` klasa ma `PrintNameOf` funkcji, można drukować nazwę każdego książki w bibliotece, chociaż może on pominąć niektóre informacje specyficzne dla typu dokumentu (liczba dla stron `Book`, liczba bajtów `HelpFile`i dlatego na).  
  
> [!NOTE]
>  Wymuszanie klasy podstawowej do wdrożenia funkcji, takich jak `PrintNameOf` często nie jest najlepszym projektu. [Funkcje wirtualne](../cpp/virtual-functions.md) oferuje inne alternatywy dla projektu.  
  
