---
title: Typy wartości (Modern C++)
ms.date: 05/07/2019
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 204ea9f86377eb8a5796f01cb81a9161163d9649
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221883"
---
# <a name="value-types-modern-c"></a>Typy wartości (Modern C++)

Klasy C++ są typami wartości domyślne. Ten temat zawiera omówienie wprowadzające typów wartości i zagadnienia odnoszące się do ich wykorzystania.

## <a name="value-vs-reference-types"></a>Wartości a typami odwołań

Jak wcześniej wspomniano, klasy C++ są typami wartości domyślne. Mogą być określone jako typy odwołań, co umożliwia zachowanie polimorficzne do obsługi obiektowy programowania. Typy wartości są wyświetlane pod względem pamięci a układ sterowania, czasami, natomiast są typy odwołań dotyczących klas podstawowych i funkcji wirtualnych do celów polimorficznych. Domyślnie typy wartości są możliwe do kopiowania, co oznacza, że zawsze istnieje Konstruktor kopiujący i operator przypisania kopiowania. Dla typów odwołań wprowadzeniu klasy niekopiowalnych (Wyłącz Konstruktor kopiujący i operator przypisania kopiowania) i użyj wirtualnego destruktora, który obsługuje ich zamierzonych polimorfizmu. Typy wartości są również związane z zawartości, które, gdy są one kopiowane zawsze zapewniają dwie niezależne wartości, które mogą być modyfikowane oddzielnie. Są typy odwołań dotyczących tożsamości — rodzaj obiektu, to jest? Z tego powodu "Typy odwołań" są również określane jako "polimorficzne typy".

Chcąc naprawdę typu przypominającego odwołania (klasy bazowej, funkcje wirtualne), należy jawnie wyłączyć kopiowania, jak pokazano na `MyRefType` klasy w poniższym kodzie.

```cpp
// cl /EHsc /nologo /W4

class MyRefType {
private:
    MyRefType & operator=(const MyRefType &);
    MyRefType(const MyRefType &);
public:
    MyRefType () {}
};

int main()
{
    MyRefType Data1, Data2;
    // ...
    Data1 = Data2;
}
```

Kompilowanie kodu powyżej powoduje następujący błąd:

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>Typy wartości i przenieść wydajność

Kopiuj alokacji obciążenie jest unikać ze względu na nowe optymalizacje kopiowania. Na przykład podczas wstawiania ciągu w środku wektor ciągi nastąpi nie kopiowania ponownej alokacji obciążenie, tylko przeniesienia — nawet wtedy, gdy powoduje zwiększania wektora, sam. Dotyczy to również inne operacje, na przykład wykonywania operacji Dodaj dwa bardzo dużych obiektów. Jak włączyć Optymalizacje te wartości operacji? W niektórych Kompilatory języka C++ kompilator umożliwi to dla Ciebie niejawnie, tak, jak konstruktory kopiujące, które mogą być automatycznie generowane przez kompilator. Jednak w C++, klasa będzie konieczne "opt-in" przeniesienia przypisania i konstruktory deklarując ją w swojej definicji klasy. Jest to realizowane za pomocą podwójnego znaku ampersand (& &) odwołanie rvalue w odpowiedniej składowej funkcji deklaracje i definiowanie konstruktora przenoszącego i przenieść przypisania metody.  Należy również wpisz poprawny kod, aby "wykradać wnętrzności" z obiektem źródłowym.

Jak można zdecydować, jeśli potrzebujesz przenieść włączone? Jeśli znasz już, że należy skopiować konstrukcji włączone, prawdopodobnie chcesz przenieść włączone, jeśli może być tańsze niż kopię głęboką. Jednak jeśli wiesz, że należy przenieść pomocy technicznej, go nie musi oznaczać, że kopia włączone. Ostatnim przypadku będzie nazywane "obsługujące tylko przenoszenie type". Na przykład już w bibliotece standardowej `unique_ptr`. Jako notatka boczna starego `auto_ptr` jest przestarzały i został zastąpiony przez `unique_ptr` dokładnie ze względu na brak obsługi semantyki przenoszenia w poprzedniej wersji języka C++.

Za pomocą semantyki przenoszenia, można wartość zwracaną lub insert-in-middle. Przeniesienie jest optymalizacja kopiowania. Ma potrzeby Alokacja sterty obejść ten problem. Należy wziąć pod uwagę poniższym pseudokodzie:

```cpp
#include <set>
#include <vector>
#include <string>
using namespace std;

//...
set<widget> LoadHugeData() {
    set<widget> ret;
    // ... load data from disk and populate ret
    return ret;
}
//...
widgets = LoadHugeData();   // efficient, no deep copy

vector<string> v = IfIHadAMillionStrings();
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)
//...
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);
//...
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies
```

### <a name="enabling-move-for-appropriate-value-types"></a>Włączanie przeniesienia dla wartości odpowiednich typów

Dla klasy podobne wartości, gdzie przenoszenia może być tańsze niż kopię głęboką należy włączyć konstrukcji przenoszenia i przenieść przypisania, w celu zwiększenia wydajności. Należy wziąć pod uwagę poniższym pseudokodzie:

```cpp
#include <memory>
#include <stdexcept>
using namespace std;
// ...
class my_class {
    unique_ptr<BigHugeData> data;
public:
    my_class( my_class&& other )   // move construction
        : data( move( other.data ) ) { }
    my_class& operator=( my_class&& other )   // move assignment
    { data = move( other.data ); return *this; }
    // ...
    void method() {   // check (if appropriate)
        if( !data )
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");
    }
};
```

Jeśli włączysz przydzielania konstrukcji kopii, również włączyć przeniesienia konstrukcji/przypisania jeśli może być tańsze niż kopię głęboką.

Niektóre *-wartość* są typy obsługujące tylko przenoszenie, takie jak kiedy nie można sklonować zasobem tylko przeniesienia własności. Przykład: `unique_ptr`.

## <a name="section"></a>`Section`

Zawartość

## <a name="see-also"></a>Zobacz także

[System typów języka C++ (Modern C++)](../cpp/cpp-type-system-modern-cpp.md)<br/>
[Witaj z powrotem w języku C++ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
