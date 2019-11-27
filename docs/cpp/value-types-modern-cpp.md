---
title: Klasy C++ jako typy wartości
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 1aabcad46e848e1a499a142adaba5002a829bbf5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246020"
---
# <a name="c-classes-as-value-types"></a>Klasy C++ jako typy wartości

C++klasy są według domyślnych typów wartości. Można je określić jako typy referencyjne, które umożliwiają zachowanie polimorficzne w celu obsługi programowania zorientowanego obiektowo. Typy wartości są czasami wyświetlane z perspektywy kontroli pamięci i układu, natomiast typy odwołań dotyczą klas bazowych i funkcji wirtualnych na potrzeby polimorficznych celów. Domyślnie typy wartości są kopiowane, co oznacza, że zawsze jest Konstruktor kopiujący i operator przypisania kopiowania. W przypadku typów referencyjnych nie można skopiować klasy (wyłączyć Konstruktor kopiujący i operator przypisania kopiowania) i użyć destruktora wirtualnego, który obsługuje zamierzony polimorfizm. Typy wartości są również związane z zawartością, która podczas kopiowania zawsze udostępnia dwie niezależne wartości, które mogą być modyfikowane osobno. Typy odwołań dotyczą tożsamości — jakiego rodzaju obiektu jest? Z tego powodu "typy referencyjne" są również określane jako "typy polimorficzne".

Jeśli naprawdę potrzebujesz typu przypominającego odwołanie (klasa bazowa, funkcje wirtualne), musisz jawnie wyłączyć kopiowanie, jak pokazano w klasie `MyRefType` w poniższym kodzie.

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

Skompilowanie powyższego kodu spowoduje następujący błąd:

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>Typy wartości i wydajność przenoszenia

Należy unikać narzutu przydziału kopii z powodu nowych optymalizacji kopiowania. Na przykład podczas wstawiania ciągu w środku wektora ciągów nie będzie można naliczać ponownego przydziału kopii, tylko wtedy, gdy spowoduje to wzrost wektora. Dotyczy to również innych operacji, na przykład podczas wykonywania operacji dodawania dla dwóch bardzo dużych obiektów. Jak włączyć te optymalizacje operacji wartości? W przypadku C++ niektórych kompilatorów kompilator włączy to dla Ciebie niejawnie, podobnie jak konstruktory kopiujące mogą być automatycznie generowane przez kompilator. Jednakże w C++, Klasa musi być "Zgoda", aby przenieść przypisanie i konstruktory przez zadeklarowanie go w definicji klasy. Jest to realizowane przy użyciu podwójnego znaku "& &) odwołania rvalue w odpowiednich deklaracjach funkcji Członkowskich i definiowania konstruktora przenoszenia i przenoszenia metod przypisywania.  Należy również wstawić poprawny kod w celu "kradzieży wnętrzności" poza obiekt źródłowy.

Jak należy zdecydować, czy jest włączone przenoszenie? Jeśli wiesz już, że jest włączona konstrukcja kopiowania, prawdopodobnie chcesz przenieść ją, jeśli może być tańsza niż Szczegółowa kopia. Jeśli jednak wiesz, że potrzebujesz wsparcia przenoszenia, nie musisz oznaczać, że kopiowanie ma być włączone. Ten ostatni przypadek zostałby wywołany "typu" tylko do przenoszenia ". Przykładem znajdującym się już w bibliotece standardowej jest `unique_ptr`. Jako notatka po stronie, stary `auto_ptr` jest przestarzały i został zastąpiony przez `unique_ptr` precyzyjnie ze względu na brak obsługi semantyki przenoszenia w poprzedniej wersji programu C++.

Używając semantyki przenoszenia, można zwrócić przez wartość lub wstawić w środku. Move to Optymalizacja kopiowania. Istnieje potrzeba przydzielenia sterty jako obejścia. Weź pod uwagę następujące pseudokodzie:

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

### <a name="enabling-move-for-appropriate-value-types"></a>Włączanie przenoszenia dla odpowiednich typów wartości

Dla klasy podobnej do wartości Move może być tańsza niż głęboka kopia, umożliwia tworzenie konstrukcji przenoszenia i przenoszenie przydziału w celu zwiększenia wydajności. Weź pod uwagę następujące pseudokodzie:

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

W przypadku włączenia tworzenia/przypisywania kopii należy również włączyć konstruowanie konstrukcji/przypisania, jeśli będzie ono tańsze niż głęboka kopia.

Niektóre typy *inne niż wartości* są tylko do przenoszenia, na przykład gdy nie można sklonować zasobu, tylko przeniesienie własności. Przykład: `unique_ptr`.

## <a name="see-also"></a>Zobacz także

[C++System typów](../cpp/cpp-type-system-modern-cpp.md)<br/>
[Zapraszamy ponownie doC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
