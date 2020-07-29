---
title: Kontrola dostępu do elementów członkowskich (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
ms.openlocfilehash: de775c511701cd0b7cf923f47e33723b30a966e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186974"
---
# <a name="member-access-control-c"></a>Kontrola dostępu do elementów członkowskich (C++)

Kontrola dostępu umożliwia oddzielenie [publicznego](../cpp/public-cpp.md) interfejsu klasy od [prywatnych](../cpp/private-cpp.md) szczegółów implementacji i [chronionych](../cpp/protected-cpp.md) elementów członkowskich, które są przeznaczone tylko do użytku przez klasy pochodne. Specyfikator dostępu stosuje się do wszystkich członków zadeklarowanych po nim do momentu napotkania następnego specyfikatora dostępu.

```cpp
class Point
{
public:
    Point( int, int ) // Declare public constructor.;
    Point();// Declare public default constructor.
    int &x( int ); // Declare public accessor.
    int &y( int ); // Declare public accessor.

private:                 // Declare private state variables.
    int _x;
    int _y;

protected:      // Declare protected function for derived classes only.
    Point ToWindowCoords();
};
```

Domyślny dostęp znajduje się **`private`** w klasie, a **`public`** w strukturze lub Unii. Specyfikatory dostępu w klasie mogą być używane dowolną liczbę razy w dowolnej kolejności. Alokacja magazynu dla obiektów typów klas jest zależna od implementacji, ale składowe są gwarantowane po przypisaniu do nich kolejnych adresów pamięci między specyfikatorami dostępu.

## <a name="member-access-control"></a>Kontrola dostępu do elementów członkowskich

|Typ dostępu|Znaczenie|
|--------------------|-------------|
|[użytek](../cpp/private-cpp.md)|Składowe klasy zadeklarowane jako **`private`** mogą być używane tylko przez funkcje członkowskie i znajomych (klasy lub funkcje) klasy.|
|[protected](../cpp/protected-cpp.md)|Składowe klasy zadeklarowane jako **`protected`** mogą być używane przez funkcje członkowskie i znajomych (klasy lub funkcje) klasy. Ponadto mogą być używane przez klasy pochodne od klasy.|
|[public](../cpp/public-cpp.md)|Składowe klasy zadeklarowane jako **`public`** mogą być używane przez dowolną funkcję.|

Kontrola dostępu pomaga uniemożliwić korzystanie z obiektów w sposób nieprzeznaczony do użycia. Ta ochrona zostaje utracona, gdy są wykonywane jawne konwersje typów (casts).

> [!NOTE]
> Kontrola dostępu jest równie stosowana dla wszystkich nazw: funkcje członkowskie, dane elementu członkowskiego, klasy zagnieżdżone i moduły wyliczające.

## <a name="access-control-in-derived-classes"></a>Access Control w klasach pochodnych

Dwa czynniki kontrolują, które składowe klasy bazowej są dostępne w klasie pochodnej; te same czynniki kontrolują dostęp do dziedziczonych elementów członkowskich w klasie pochodnej:

- Czy Klasa pochodna deklaruje klasę bazową przy użyciu **`public`** specyfikatora dostępu.

- Jaki jest dostęp do elementu członkowskiego w klasie bazowej.

W poniższej tabeli przedstawiono interakcje między tymi czynnikami i sposób określania dostępu do elementu członkowskiego klasy podstawowej.

### <a name="member-access-in-base-class"></a>Dostęp do elementu członkowskiego w klasie bazowej

|private|protected|Publiczny|
|-------------|---------------|------------|
|Zawsze niedostępna niezależnie od dostępu do wartości pochodnych|Prywatna w klasie pochodnej, jeśli używasz użycia prywatnego|Prywatna w klasie pochodnej, jeśli używasz użycia prywatnego|
||Chroniona w klasie pochodnej, jeśli używasz ochrony pochodnej|Chroniona w klasie pochodnej, jeśli używasz ochrony pochodnej|
||Chronione w klasie pochodnej, jeśli używasz publicznego wyprowadzenia|Public in klasy pochodnej, jeśli używasz publicznego wyprowadzenia|

Zostało to przedstawione w poniższym przykładzie:

```cpp
// access_specifiers_for_base_classes.cpp
class BaseClass
{
public:
    int PublicFunc(); // Declare a public member.
protected:
    int ProtectedFunc(); // Declare a protected member.
private:
    int PrivateFunc(); // Declare a private member.
};

// Declare two classes derived from BaseClass.
class DerivedClass1 : public BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

class DerivedClass2 : private BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

int main()
{
    DerivedClass1 derived_class1;
    DerivedClass2 derived_class2;
    derived_class1.PublicFunc();
    derived_class2.PublicFunc(); // function is inaccessible
}
```

W programie `DerivedClass1` funkcja członkowska `PublicFunc` jest publiczną składową i `ProtectedFunc` jest chronionym elementem członkowskim, ponieważ `BaseClass` jest publiczną klasą bazową. `PrivateFunc`jest prywatny dla `BaseClass` i nie jest dostępny dla żadnej klasy pochodnej.

W programie `DerivedClass2` funkcje `PublicFunc` i `ProtectedFunc` są uznawane za prywatne składowe, ponieważ `BaseClass` jest prywatną klasą bazową. `PrivateFunc`Jest on ponownie prywatny `BaseClass` i nie jest dostępny dla żadnej klasy pochodnej.

Można zadeklarować klasę pochodną bez specyfikatora dostępu klasy bazowej. W takim przypadku pochodny jest uznawany za prywatny, jeśli deklaracja klasy pochodnej używa **`class`** słowa kluczowego. Wartość pochodna jest uznawana za publiczną, jeśli deklaracja klasy pochodnej używa **`struct`** słowa kluczowego. Na przykład następujący kod:

```cpp
class Derived : Base
...
```

jest równoważne:

```cpp
class Derived : private Base
...
```

Podobnie, poniższy kod:

```cpp
struct Derived : Base
...
```

jest równoważne:

```cpp
struct Derived : public Base
...
```

Należy zauważyć, że składowe zadeklarowane jako mające dostęp prywatny nie są dostępne dla funkcji ani klas pochodnych, chyba że te funkcje lub klasy są deklarowane przy użyciu **`friend`** deklaracji w klasie bazowej.

**`union`** Typ nie może mieć klasy bazowej.

> [!NOTE]
> Podczas określania prywatnej klasy bazowej zaleca się jawne użycie **`private`** słowa kluczowego, aby użytkownicy klasy pochodnej zrozumieć dostęp do elementu członkowskiego.

## <a name="access-control-and-static-members"></a>Kontrola dostępu i statyczne elementy członkowskie

Po określeniu klasy bazowej jako **`private`** ma ona wpływ tylko na niestatyczne elementy członkowskie. Publiczne statyczne elementy członkowskie są nadal dostępne w klasach pochodnych. Jednak dostęp do elementów członkowskich klasy podstawowej przy użyciu wskaźników, odwołań lub obiektów może wymagać konwersji, podczas gdy kontrola dostępu jest ponownie stosowana. Rozpatrzmy następujący przykład:

```cpp
// access_control.cpp
class Base
{
public:
    int Print();             // Nonstatic member.
    static int CountOf();    // Static member.
};

// Derived1 declares Base as a private base class.
class Derived1 : private Base
{
};
// Derived2 declares Derived1 as a public base class.
class Derived2 : public Derived1
{
    int ShowCount();    // Nonstatic member.
};
// Define ShowCount function for Derived2.
int Derived2::ShowCount()
{
   // Call static member function CountOf explicitly.
    int cCount = Base::CountOf();     // OK.

   // Call static member function CountOf using pointer.
    cCount = this->CountOf();  // C2247. Conversion of
                               //  Derived2 * to Base * not
                               //  permitted.
    return cCount;
}
```

W poprzednim kodzie kontrola dostępu uniemożliwia konwersję ze wskaźnika do `Derived2` wskaźnika do `Base` . **`this`** Wskaźnik jest niejawnie typu `Derived2 *` . Aby wybrać `CountOf` funkcję, **`this`** należy przekonwertować ją na typ `Base *` . Taka konwersja nie jest dozwolona, ponieważ `Base` jest prywatną pośrednią klasą bazową `Derived2` . Konwersja na typ prywatnej klasy bazowej jest akceptowalna tylko dla wskaźników do bezpośrednich klas pochodnych. W związku z tym wskaźniki typu `Derived1 *` mogą być konwertowane na typ `Base *` .

Należy zauważyć, że wywołanie `CountOf` funkcji jawnie, bez użycia wskaźnika, odwołania lub obiektu, aby go zaznaczyć, oznacza brak konwersji. W związku z tym wywołanie jest dozwolone.

Elementy członkowskie i znajomi klasy pochodnej, `T` mogą konwertować wskaźnik na `T` wskaźnik do klasy bazowej bezpośredniej `T` .

## <a name="access-to-virtual-functions"></a>Dostęp do funkcji wirtualnych

Kontrola dostępu zastosowana do funkcji [wirtualnych](../cpp/virtual-cpp.md) jest określana na podstawie typu używanego do wywołania funkcji. Zastępowanie deklaracji funkcji nie ma wpływu na kontrolę dostępu dla danego typu. Na przykład:

```cpp
// access_to_virtual_functions.cpp
class VFuncBase
{
public:
    virtual int GetState() { return _state; }
protected:
    int _state;
};

class VFuncDerived : public VFuncBase
{
private:
    int GetState() { return _state; }
};

int main()
{
   VFuncDerived vfd;             // Object of derived type.
   VFuncBase *pvfb = &vfd;       // Pointer to base type.
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.
   int State;

   State = pvfb->GetState();     // GetState is public.
   State = pvfd->GetState();     // C2248 error expected; GetState is private;
}
```

W poprzednim przykładzie wywołanie funkcji wirtualnej `GetState` przy użyciu wskaźnika do typu `VFuncBase` wywołań `VFuncDerived::GetState` i `GetState` jest traktowane jako publiczne. Jednak wywoływanie `GetState` przy użyciu wskaźnika do typu `VFuncDerived` jest naruszeniem kontroli dostępu, ponieważ `GetState` jest zadeklarowana jako prywatna w klasie `VFuncDerived` .

> [!CAUTION]
> Funkcja wirtualna `GetState` może być wywoływana przy użyciu wskaźnika do klasy bazowej `VFuncBase` . Nie oznacza to, że wywoływana funkcja jest wersją klasy bazowej tej funkcji.

## <a name="access-control-with-multiple-inheritance"></a>Kontrola dostępu z wieloma dziedziczeniem

W przypadku wielokrotnego dziedziczenia lattices obejmującego wirtualne klasy bazowe dana nazwa może być powiązana z więcej niż jedną ścieżką. Ponieważ różnej kontroli dostępu można zastosować wraz z różnymi ścieżkami, kompilator wybiera ścieżkę, która zapewnia największy dostęp. Zobacz poniższą ilustrację.

![Dostęp wzdłuż ścieżki grafu dziedziczenia](../cpp/media/vc38v91.gif "Dostęp wzdłuż ścieżki grafu dziedziczenia") <br/>
Dostęp wzdłuż ścieżki grafu dziedziczenia

Na rysunku nazwa zadeklarowana w klasie `VBase` jest zawsze osiągana przez klasę `RightPath` . Właściwa ścieżka jest bardziej dostępna `RightPath` , ponieważ deklaruje `VBase` jako publiczną klasę bazową, natomiast `LeftPath` deklaruje `VBase` jako prywatną.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)
