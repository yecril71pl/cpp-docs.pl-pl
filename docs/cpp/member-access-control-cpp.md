---
title: Kontrola dostępu do elementów członkowskich (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
ms.openlocfilehash: e8f62e82ebb7fcc18be5ac7d203df0fb46c9b635
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369856"
---
# <a name="member-access-control-c"></a>Kontrola dostępu do elementów członkowskich (C++)

Formanty dostępu umożliwiają oddzielenie interfejsu [publicznego](../cpp/public-cpp.md) klasy od szczegółów implementacji [prywatnej](../cpp/private-cpp.md) i [chronionych](../cpp/protected-cpp.md) elementów członkowskich, które są tylko do użytku przez klasy pochodne. Specyfikator dostępu ma zastosowanie do wszystkich elementów członkowskich zadeklarowanych po nim, dopóki nie zostanie napotkany specyfikator dostępu następnego.

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

Domyślny dostęp jest **prywatny** w klasie i **publiczny** w strukturze lub unii. Specyfikatory dostępu w klasie mogą być używane dowolną liczbę razy w dowolnej kolejności. Alokacja magazynu dla obiektów typów klas jest zależna od implementacji, ale członkowie mają gwarancję, że będą przypisywane kolejno wyższe adresy pamięci między specyfikatorami dostępu.

## <a name="member-access-control"></a>Kontrola dostępu do elementów członkowskich

|Typ dostępu|Znaczenie|
|--------------------|-------------|
|[private](../cpp/private-cpp.md)|Członkowie klasy zadeklarowane jako **prywatne** mogą być używane tylko przez funkcje członkowskie i znajomych (klasy lub funkcje) klasy.|
|[protected](../cpp/protected-cpp.md)|Elementy członkowskie klasy **zadeklarowane** jako chronione mogą być używane przez funkcje członkowskie i znajomych (klasy lub funkcje) klasy. Ponadto mogą być używane przez klasy pochodzące z klasy.|
|[public](../cpp/public-cpp.md)|Elementy członkowskie klasy zadeklarowane jako **publiczne** mogą być używane przez dowolną funkcję.|

Kontrola dostępu pomaga zapobiec używaniu obiektów w sposób, który nie był przeznaczony do użycia. Ta ochrona jest tracona podczas konwersji typu jawnego (rzuty) są wykonywane.

> [!NOTE]
> Kontrola dostępu ma również zastosowanie do wszystkich nazw: funkcji członkowskich, danych członkowskich, klas zagnieżdżonych i wyliczaczy.

## <a name="access-control-in-derived-classes"></a>Kontrola dostępu w klasach pochodnych

Dwa czynniki kontrolują, które elementy członkowskie klasy podstawowej są dostępne w klasie pochodnej; te same czynniki kontrolują dostęp do dziedziczonych elementów członkowskich w klasie pochodnej:

- Czy klasa pochodna deklaruje klasę podstawową przy użyciu specyfikatora dostępu **publicznego.**

- Co dostęp do elementu członkowskiego jest w klasie podstawowej.

W poniższej tabeli przedstawiono interakcję między tymi czynnikami i jak określić dostęp do elementów członkowskich klasy podstawowej.

### <a name="member-access-in-base-class"></a>Dostęp do elementu członkowskiego w klasie podstawowej

|private|protected|Public|
|-------------|---------------|------------|
|Zawsze niedostępne niezależnie od dostępu do wyprowadzania|Prywatne w klasie pochodnej, jeśli używasz prywatnego wyprowadzania|Prywatne w klasie pochodnej, jeśli używasz prywatnego wyprowadzania|
||Chronione w klasie pochodnej, jeśli używasz chronionego wyprowadzania|Chronione w klasie pochodnej, jeśli używasz chronionego wyprowadzania|
||Chronione w klasie pochodnej, jeśli używasz publicznego wyprowadzania|Publiczne w klasie pochodnej, jeśli używasz publicznego wyprowadzania|

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

W `DerivedClass1`funkcji elementu `PublicFunc` członkowskiego jest `ProtectedFunc` elementem publicznym i `BaseClass` jest chronionym elementem członkowskim, ponieważ jest publiczną klasą podstawową. `PrivateFunc`jest prywatny `BaseClass`do , i jest niedostępny dla wszystkich klas pochodnych.

W `DerivedClass2`, `PublicFunc` funkcje i `ProtectedFunc` są `BaseClass` uważane za członków prywatnych, ponieważ jest prywatną klasą podstawową. Ponownie, `PrivateFunc` jest `BaseClass`prywatny do , i jest niedostępny dla wszystkich klas pochodnych.

Można zadeklarować klasę pochodną bez specyfikatora dostępu klasy podstawowej. W takim przypadku wyprowadzanie jest uważane za prywatne, jeśli deklaracja klasy pochodnej używa słowa kluczowego **class.** Wyprowadzanie jest uważane za publiczne, jeśli deklaracja klasy pochodnej używa słowa kluczowego **struct.** Na przykład następujący kod:

```cpp
class Derived : Base
...
```

odpowiada:

```cpp
class Derived : private Base
...
```

Podobnie następujący kod:

```cpp
struct Derived : Base
...
```

odpowiada:

```cpp
struct Derived : public Base
...
```

Należy zauważyć, że elementy członkowskie zadeklarowane jako posiadające dostęp prywatny nie są dostępne dla funkcji lub klas pochodnych, chyba że te funkcje lub klasy są zadeklarowane przy użyciu deklaracji **przyjaciela** w klasie podstawowej.

Typ **unii** nie może mieć klasy podstawowej.

> [!NOTE]
> Podczas określania prywatnej klasy podstawowej, wskazane jest jawne użycie **prywatnego** słowa kluczowego, aby użytkownicy klasy pochodnej rozumieli dostęp do elementu członkowskiego.

## <a name="access-control-and-static-members"></a>Kontrola dostępu i elementy statyczne

Po określeniu klasy podstawowej jako **prywatnej**wpływa ona tylko na elementy członkowskie niestatyczne. Publiczne statyczne elementy członkowskie są nadal dostępne w klasach pochodnych. Jednak dostęp do elementów członkowskich klasy podstawowej przy użyciu wskaźników, odwołań lub obiektów może wymagać konwersji, w którym to czasie kontrola dostępu jest ponownie stosowana. Rozważmy następujący przykład:

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

W poprzednim kodzie kontrola dostępu zabrania konwersji `Derived2` ze wskaźnika na wskaźnik do `Base`. **Ten** wskaźnik jest niejawnie typu `Derived2 *`. Aby wybrać `CountOf` funkcję, należy **ją** przekonwertować na typ `Base *`. Taka konwersja nie jest `Base` dozwolona, ponieważ `Derived2`jest prywatną pośrednią klasą podstawową do . Konwersja do prywatnego typu klasy podstawowej jest dopuszczalna tylko dla wskaźników do klas pochodnych natychmiastowych. W związku z tym `Derived1 *` wskaźniki typu można `Base *`przekonwertować na typ .

Należy zauważyć, `CountOf` że wywołanie funkcji jawnie, bez użycia wskaźnika, odwołania lub obiektu, aby ją zaznaczyć, nie oznacza konwersji. W związku z tym wywołanie jest dozwolone.

Członkowie i przyjaciele klasy `T`pochodnej, można przekonwertować wskaźnik na `T` wskaźnik `T`do prywatnej bezpośredniej klasy podstawowej .

## <a name="access-to-virtual-functions"></a>Dostęp do funkcji wirtualnych

Kontrola dostępu stosowana do funkcji [wirtualnych](../cpp/virtual-cpp.md) jest określana przez typ używany do wywołania funkcji. Nadrzędne deklaracje funkcji nie mają wpływu na kontrolę dostępu dla danego typu. Przykład:

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

W poprzednim przykładzie wywołanie `GetState` funkcji wirtualnej `VFuncBase` przy `VFuncDerived::GetState`użyciu `GetState` wskaźnika do wpisywania wywołań i jest traktowane jako publiczne. Jednak `GetState` wywołanie przy użyciu `VFuncDerived` wskaźnika do typu `GetState` jest naruszeniem `VFuncDerived`kontroli dostępu, ponieważ jest zadeklarowany jako prywatny w klasie .

> [!CAUTION]
> Funkcję `GetState` wirtualną można wywołać za pomocą `VFuncBase`wskaźnika do klasy podstawowej . Nie oznacza to, że funkcja wywoływana jest wersją klasy podstawowej tej funkcji.

## <a name="access-control-with-multiple-inheritance"></a>Kontrola dostępu z wieloma dziedziczeniami

W sieciach dziedziczenia wielokrotnego obejmujących wirtualne klasy podstawowe można uzyskać pod uwagę nazwę za pośrednictwem więcej niż jednej ścieżki. Ponieważ różne kontroli dostępu mogą być stosowane wzdłuż tych różnych ścieżek, kompilator wybiera ścieżkę, która daje najwięcej dostępu. Zobacz poniższą ilustrację.

![Dostęp wzdłuż ścieżek wykresu dziedziczenia](../cpp/media/vc38v91.gif "Dostęp wzdłuż ścieżek wykresu dziedziczenia") <br/>
Dostęp wzdłuż ścieżek wykresu dziedziczenia

Na rysunku nazwa zadeklarowana `VBase` w klasie `RightPath`jest zawsze osiągana za pośrednictwem klasy . Właściwa ścieżka jest `RightPath` bardziej `VBase` dostępna, ponieważ deklaruje jako `LeftPath` publiczną klasę podstawową, podczas gdy deklaruje `VBase` jako prywatny.

## <a name="see-also"></a>Zobacz też

[Odwołanie do języka języka C++](../cpp/cpp-language-reference.md)
