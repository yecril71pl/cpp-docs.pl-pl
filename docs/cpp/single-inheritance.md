---
title: Pojedyncze dziedziczenie
ms.date: 11/04/2016
helpviewer_keywords:
- single inheritance
- base classes [C++], indirect
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- derived classes [C++], single base class
- inheritance, single
ms.assetid: 1cb946ed-8b1b-4cf1-bde0-d9cecbfdc622
ms.openlocfilehash: a188780201c00451b125288b37c7c62fbe2322c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461857"
---
# <a name="single-inheritance"></a>Pojedyncze dziedziczenie

W "pojedyncze dziedziczenie," wspólnej formy dziedziczenie, klasy mają tylko jedną klasę bazową. Należy wziąć pod uwagę relację przedstawiono na poniższej ilustracji.

![Jednym z podstawowych&#45;Wykres dziedziczenia](../cpp/media/vc38xj1.gif "vc38XJ1") prostą Grafową pojedyncze dziedziczenie

Należy pamiętać, postępu z ogólnych do określonych na rysunku. Inny wspólny atrybut znaleziono w projekcie większość hierarchie klasy to klasa pochodna zawiera "rodzaju" relacji z klasy bazowej. Na rysunku `Book` jest rodzajem elementu `PrintedDocument`i `PaperbackBook` jest rodzajem elementu `book`.

Jeden element notatki na rysunku: `Book` jest zarówno klasę pochodną (z `PrintedDocument`) i klasę bazową (`PaperbackBook` jest tworzony na podstawie `Book`). W poniższym przykładzie pokazano deklaracji szkieletowych hierarchii klas:

```cpp
// deriv_SingleInheritance.cpp
// compile with: /LD
class PrintedDocument {};

// Book is derived from PrintedDocument.
class Book : public PrintedDocument {};

// PaperbackBook is derived from Book.
class PaperbackBook : public Book {};
```

`PrintedDocument` jest uznawany za "bezpośredniej klasy podstawowej" klasy `Book`; jest klasy "pośrednią podstawą" `PaperbackBook`. Różnica jest bezpośrednią klasą bazową jest wyświetlana na liście podstawowej deklaracji klasy i nie ma pośrednią podstawą.

Klasa bazowa, z którego pochodzi każdej klasy jest zadeklarowana przed deklaracją klasy pochodnej. Nie jest wystarczające, aby zapewnić deklarację odwołujące się do przodu dla klasy bazowej; musi być pełną deklarację.

W powyższym przykładzie specyfikatora dostępu **publicznych** jest używany. Znaczenie publicznych, chronionych i prywatnych dziedziczenia opisano w [kontroli dostępu do elementu członkowskiego.](../cpp/member-access-control-cpp.md)

Klasa może służyć jako klasa bazowa dla wielu określonych klas, jak pokazano na poniższej ilustracji.

![Grafie acyklicznym wskazówkami](../cpp/media/vc38xj2.gif "vc38XJ2") próbki z kierowane grafie Acyklicznym

Na diagramie powyżej o nazwie "skierowanym grafie acyklicznym" (lub "DAG"), niektóre z klas są klasy bazowe dla klasy pochodnej więcej niż jeden. Jednakże, odwrotna sytuacja nie jest wartość true: istnieje tylko jeden bezpośrednią klasą bazową dla dowolnej podanej klasy pochodnej. Wykres na rysunku przedstawiono strukturę "pojedyncze dziedziczenie".

> [!NOTE]
>  Grafy acykliczne ukierunkowanej nie są unikatowe dla pojedyncze dziedziczenie. Służą one również opisujący wykresy dziedziczenia wielokrotnego.

W dziedziczenie Klasa pochodna zawiera elementy członkowskie klasy bazowej, a także nowych elementów członkowskich, które można dodać. W rezultacie klasy pochodnej może odwoływać się do elementów członkowskich klasy podstawowej, (chyba że te elementy członkowskie są ponownie zdefiniowana w klasie pochodnej). Operator rozpoznawania zakresu (`::`) może służyć do odwoływania się do elementów członkowskich bezpośredniej lub pośredniej klasy bazowej, gdy tych członków mają został ponownie zdefiniowana w klasie pochodnej. Rozważmy następujący przykład:

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

Należy pamiętać, że Konstruktor `Book`, (`Book::Book`), ma dostęp do składowej danych `Name`. W programie do obiektu typu `Book` mogą być tworzone i używane w następujący sposób:

```cpp
//  Create a new object of type Book. This invokes the
//   constructor Book::Book.
Book LibraryBook( "Programming Windows, 2nd Ed", 944 );

...

//  Use PrintNameOf function inherited from class Document.
LibraryBook.PrintNameOf();
```

Jak pokazano w powyższym przykładzie oraz funkcji składowej klasy i danych dziedziczonych służą identycznie. Jeśli Implementacja klasy `Book` wywołuje reimplementation z `PrintNameOf` funkcji, funkcja, która należy do `Document` klasy, które można wywołać tylko przy użyciu rozpoznawania zakresu (`::`) — operator:

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

Wskaźniki i odwołania do klasy pochodne mogą być niejawnie konwertowane do wskaźników i odwołań pozwalającą na ich klasami podstawowymi Jeśli jest dostępny, jednoznaczną klasy bazowej. Poniższy kod ilustruje tę koncepcję za pomocą wskaźników (ta sama zasada dotyczy odwołania):

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

W powyższym przykładzie są tworzone różne typy. Jednakże ponieważ te typy są uzyskiwane z `Document` klasy, jest niejawną konwersję do `Document *`. W rezultacie `DocLib` jest "Lista heterogenicznych" (w którym nie wszystkie obiekty są tego samego typu lista) zawierający różnymi rodzajami obiektów.

Ponieważ `Document` klasa ma `PrintNameOf` funkcji, można wydrukować nazwę każdej książki w bibliotece, chociaż może je pominąć niektóre informacje specyficzne dla typu dokumentu (liczba dla stron `Book`, liczbę bajtów w przypadku `HelpFile`, a tym samym Funkcja włączona).

> [!NOTE]
>  Wymuszanie klasę bazową do implementacji funkcji, takich jak `PrintNameOf` często nie jest najlepszy projekt. [Funkcje wirtualne](../cpp/virtual-functions.md) oferuje inne alternatywy dla projektu.