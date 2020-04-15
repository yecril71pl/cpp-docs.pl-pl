---
title: Pojedyncze dziedziczenie
ms.date: 11/19/2018
helpviewer_keywords:
- single inheritance
- base classes [C++], indirect
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- derived classes [C++], single base class
- inheritance, single
ms.assetid: 1cb946ed-8b1b-4cf1-bde0-d9cecbfdc622
ms.openlocfilehash: 8fe141886fd5087b71484368c0f79d62238f7f22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365610"
---
# <a name="single-inheritance"></a>Pojedyncze dziedziczenie

W "pojedynczego dziedziczenia", wspólnej formie dziedziczenia, klasy mają tylko jedną klasę podstawową. Należy wziąć pod uwagę relację zilustrowaną na poniższej ilustracji.

![Podstawowy wykres dziedziczenia pojedynczego&#45;](../cpp/media/vc38xj1.gif "Podstawowy wykres dziedziczenia pojedynczego&#45;") <br/>
Prosty wykres pojedynczego dziedziczenia

Zwróć uwagę na postęp od ogólnego do specyficznego na rysunku. Innym typowym atrybutem znalezionym w projekcie większości hierarchii klas jest to, że klasa pochodna ma relację "rodzaj" z klasą podstawową. Na rysunku, `Book` jest rodzajem `PrintedDocument`, `PaperbackBook` i jest rodzajem `book`.

Inny element uwagi na `Book` rysunku: jest zarówno klasą pochodną (od `PrintedDocument`) jak i klasą podstawową (`PaperbackBook` pochodzi od `Book`). Szkieletowa deklaracja takiej hierarchii klas jest pokazana w poniższym przykładzie:

```cpp
// deriv_SingleInheritance.cpp
// compile with: /LD
class PrintedDocument {};

// Book is derived from PrintedDocument.
class Book : public PrintedDocument {};

// PaperbackBook is derived from Book.
class PaperbackBook : public Book {};
```

`PrintedDocument`jest uważany za klasę "bezpośrednią bazę" do; `Book` jest to klasa "pośrednia `PaperbackBook`podstawa" do . Różnica polega na tym, że bezpośrednia klasa podstawowa pojawia się na liście podstawowej deklaracji klasy, a podstawa pośrednia nie.

Klasa podstawowa, z której pochodzi każda klasa, jest deklarowana przed deklaracją klasy pochodnej. Nie jest wystarczające, aby zapewnić deklarację odwołującą się do przodu dla klasy podstawowej; musi to być pełna deklaracja.

W poprzednim przykładzie jest używany specyfikator dostępu **publicznych.** Znaczenie dziedziczenia publicznego, chronionego i prywatnego jest opisane w [kontroli dostępu do elementu członkowskiego.](../cpp/member-access-control-cpp.md)

Klasa może służyć jako klasa podstawowa dla wielu określonych klas, jak pokazano na poniższym rysunku.

![Wykres acykliczny skierowany](../cpp/media/vc38xj2.gif "Wykres acykliczny skierowany") <br/>
Próbka reżyserii wykresu acyklicznego

Na diagramie pokazanym powyżej, o nazwie "skierowane wykres acykliczny" (lub "DAG"), niektóre klasy są klasy podstawowe dla więcej niż jednej klasy pochodnej. Jednak odwrotnie nie jest prawdą: istnieje tylko jedna bezpośrednia klasa podstawowa dla danej klasy pochodnej. Wykres na rysunku przedstawia strukturę "pojedynczego dziedziczenia".

> [!NOTE]
> Ukierunkowane wykresy acykliczne nie są unikatowe dla pojedynczego dziedziczenia. Są one również używane do przedstawiania wykresów wielokrotnego dziedziczenia.

W dziedziczeniu klasa pochodna zawiera członków klasy podstawowej oraz wszystkie nowe elementy członkowskie, które można dodać. W rezultacie klasa pochodna może odwoływać się do członków klasy podstawowej (chyba że te elementy członkowskie są ponownie zdefiniowane w klasie pochodnej). Operator rozpoznawania zakresu`::`( ) może służyć do odwoływania się do elementów członkowskich klas podstawowych bezpośrednich lub pośrednich, gdy te elementy członkowskie zostały ponownie zdefiniowane w klasie pochodnej. Rozważmy następujący przykład:

```cpp
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

Należy zauważyć, że `Book`konstruktor dla ,`Book::Book`( `Name`), ma dostęp do elementu członkowskiego danych, . W programie obiekt typu `Book` może być tworzony i używany w następujący sposób:

```cpp
//  Create a new object of type Book. This invokes the
//   constructor Book::Book.
Book LibraryBook( "Programming Windows, 2nd Ed", 944 );

...

//  Use PrintNameOf function inherited from class Document.
LibraryBook.PrintNameOf();
```

Jak pokazano w poprzednim przykładzie, class-member i dziedziczone dane i funkcje są używane identycznie. Jeśli implementacja `Book` dla klasy wymaga ponownego wdrożenia `PrintNameOf` funkcji, funkcja, która należy `Document` do klasy można wywołać tylko`::`za pomocą operatora scope-resolution ( ):

```cpp
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

Wskaźniki i odwołania do klas pochodnych mogą być niejawnie konwertowane na wskaźniki i odwołania do ich klas podstawowych, jeśli istnieje dostępna, jednoznaczna klasa podstawowa. Poniższy kod demonstruje tę koncepcję przy użyciu wskaźników (ta sama zasada ma zastosowanie do odwołań):

```cpp
// deriv_SingleInheritance4.cpp
// compile with: /W3
struct Document {
   char *Name;
   void PrintNameOf() {}
};

class PaperbackBook : public Document {};

int main() {
   Document * DocLib[10];   // Library of ten documents.
   for (int i = 0 ; i < 5 ; i++)
      DocLib[i] = new Document;
   for (int i = 5 ; i < 10 ; i++)
      DocLib[i] = new PaperbackBook;
}
```

W poprzednim przykładzie tworzone są różne typy. Jednak ponieważ wszystkie te typy `Document` pochodzą z klasy, istnieje `Document *`niejawna konwersja do . W rezultacie `DocLib` jest "heterogeniią" (lista, w której nie wszystkie obiekty są tego samego typu) zawierające różne rodzaje obiektów.

Ponieważ `Document` klasa ma `PrintNameOf` funkcję, może wydrukować nazwę każdej książki w bibliotece, chociaż może pominąć niektóre informacje specyficzne `Book`dla typu dokumentu `HelpFile`(liczba stron dla , liczba bajtów dla , i tak dalej).

> [!NOTE]
> Wymuszanie klasy podstawowej do `PrintNameOf` zaimplementowania funkcji, takiej jak często nie jest najlepszym projektem. [Funkcje wirtualne](../cpp/virtual-functions.md) oferują inne alternatywy projektowe.
