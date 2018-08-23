---
title: Kontrola dostępu do składowych (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b2cff8470ad11270d2f40abf3d03c708a9d6e87
ms.sourcegitcommit: 9035b4df448583c195f54318e941284b632dc308
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464549"
---
# <a name="member-access-control-c"></a>Kontrola dostępu do elementów członkowskich (C++)
Mechanizmy kontroli dostępu umożliwiają oddzielenie [publicznych](../cpp/public-cpp.md) interfejsu klasy z [prywatnej](../cpp/private-cpp.md) szczegółów implementacji i [chronione](../cpp/protected-cpp.md) elementów członkowskich, które służą tylko do użycia przez klasy pochodne. Specyfikator dostępu ma zastosowanie do wszystkich elementów członkowskich zadeklarowanych po nim, dopóki nie zostanie osiągnięty następnego specyfikatora dostępu.  
  
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
  
 Dostęp do domyślnej jest **prywatnej** w klasie i **publicznych** w strukturze lub Unii. Specyfikatory dostępu w klasie mogą być używane z dowolną liczbę razy w dowolnej kolejności. Alokacja pamięci dla obiektów typów klasy jest zależy od implementacji, ale elementy członkowskie są gwarantowane przypisanie kolejno adresów pamięci między specyfikatory dostępu.  
  
### <a name="member-access-control"></a>Kontrola dostępu do elementów członkowskich  
  
|Typ dostępu|Znaczenie|  
|--------------------|-------------|  
|[private](../cpp/private-cpp.md)|Składowe klasy zadeklarowane jako **prywatnej** mogą być używane tylko przez funkcje składowe i znajomych (klas lub funkcji) klasy.|  
|[protected](../cpp/protected-cpp.md)|Składowe klasy zadeklarowane jako **chronione** może służyć przez funkcje składowe i znajomych (klas lub funkcji) klasy. Ponadto może być używany przez klasy pochodne klasy.|  
|[public](../cpp/public-cpp.md)|Składowe klasy zadeklarowane jako **publicznych** może być używana przez funkcję.|  
  
 Kontrola dostępu ułatwia zapobieganie przy użyciu obiektów w sposób, który nie były przeznaczone do użycia. Ta ochrona jest utracone w przypadku, gdy wykonywane są Konwersje jawne (rzutowania).  
  
> [!NOTE]
>  Kontrola dostępu jest równie mające zastosowanie do wszystkich nazw: elementów członkowskich, element członkowski danych, klasy zagnieżdżone i modułów wyliczających.  
  
## <a name="access-control-in-derived-classes"></a>Kontrola dostępu w klasach pochodnych  
 Kontrolka dwa czynniki, które elementy członkowskie klasy bazowej są dostępne w klasie pochodnej; tych samych czynników kontroli dostępu do dziedziczone elementy członkowskie klasy pochodnej:  
  
-   Czy pochodne klasy deklaruje, przy użyciu klasy bazowej **publicznych** specyfikatorze dostępu.  
  
-   Dostęp do elementu członkowskiego nowości w klasie bazowej.  
  
 W poniższej tabeli przedstawiono interakcje między te czynniki oraz sposobu określania dostęp do składowej klasy bazowej.  
  
### <a name="member-access-in-base-class"></a>Dostęp do elementu członkowskiego w klasie bazowej  
  
|private|protected|Public|  
|-------------|---------------|------------|  
|Zawsze niedostępny, niezależnie od dostępu tworzenie wartości pochodnych|Prywatna w klasie pochodnej, korzystając z prywatnego tworzenie wartości pochodnych|Prywatna w klasie pochodnej, korzystając z prywatnego tworzenie wartości pochodnych|  
||Chronione w klasie pochodnej, jeśli używasz pochodnym chronionych|Chronione w klasie pochodnej, jeśli używasz pochodnym chronionych|  
||Chronione w klasie pochodnej, jeśli używasz pochodnym publiczny|Jest publiczna w klasie pochodnej, jeśli używasz publicznego tworzenie wartości pochodnych|  
  
 Ilustruje to poniższy przykład:  
  
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
  
 W `DerivedClass1`, funkcja elementu członkowskiego `PublicFunc` jest elementem członkowskim publicznych i `ProtectedFunc` jest chroniony element członkowski, ponieważ `BaseClass` będąca klasą bazową publicznych. `PrivateFunc` jest oznaczony jako prywatny `BaseClass`, i jest niedostępna dla dowolnej klasy pochodnej.  
  
 W `DerivedClass2`, funkcje `PublicFunc` i `ProtectedFunc` są uznawane za prywatne składowe, ponieważ `BaseClass` będąca klasą bazową prywatnych. Ponownie `PrivateFunc` są prywatne `BaseClass`, i jest niedostępna dla dowolnej klasy pochodnej.  
  
 Można zadeklarować klasy pochodnej bez specyfikatora dostępu do klasy bazowej. W takim przypadku informacje o pochodzeniu jest uznawane za prywatne, jeśli używa deklaracji klasy pochodnej **klasy** — słowo kluczowe. Informacje o pochodzeniu jest uważana za publiczne, jeśli używa deklaracji klasy pochodnej **struktury** — słowo kluczowe. Na przykład poniższy kod:  
  
```cpp 
class Derived : Base  
...  
```  
  
 jest równoważne:  
  
```cpp 
class Derived : private Base  
...  
```  
  
 Podobnie poniższy kod:  
  
```cpp 
struct Derived : Base  
...  
```  
  
 jest równoważne:  
  
```cpp 
struct Derived : public Base  
...  
```  
  
 Należy pamiętać, że składowych zadeklarowanych jako posiadające prywatny dostęp nie są dostępne dla funkcji lub klasy pochodne, chyba że tych funkcji lub klasy są deklarowane przy użyciu **friend** deklaracji w klasie bazowej.  
  
 A **Unii** typ nie może mieć klasy bazowej.  
  
> [!NOTE]
>  Podczas określania prywatnych klasy bazowej, zaleca się jawnie użyć **prywatnej** — słowo kluczowe, aby użytkownicy klasy pochodnej poznanie dostęp do elementu członkowskiego.  
  
## <a name="access-control-and-static-members"></a>Kontrola dostępu i statyczne elementy członkowskie  
 Po określeniu klasy bazowej jako **prywatnej**, ma wpływ tylko niestatycznych elementów członkowskich. Publiczne statyczne elementy członkowskie są nadal dostępne w klasach pochodnych. Jednakże uzyskiwania dostępu do członków klasy podstawowej za pomocą wskaźników, odwołań lub obiektów może wymagać konwersji, w tym czasie kontroli dostępu jest ponownie stosowana. Rozważmy następujący przykład:  
  
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
  
 W poprzednim kodzie kontroli dostępu zabrania konwersja ze wskaźnika do `Derived2` na wskaźnik do `Base`. **To** wskaźnik jest niejawnie typu `Derived2 *`. Aby wybrać `CountOf` funkcji **to** musi być konwertowany na typ `Base *`. Taka konwersja nie jest dozwolona, ponieważ `Base` jest prywatny pośrednią klasą bazową do `Derived2`. Konwersja na typ klasy bazowej prywatnego jest dopuszczalne tylko dla wskaźników do natychmiastowego klas pochodnych. W związku z tym, wskaźników typu `Derived1 *` można przekonwertować na typ `Base *`.  
  
 Należy pamiętać, że wywołanie `CountOf` funkcja jawnie, bez używania wskaźnik, odwołanie lub obiekt, aby go zaznaczyć, oznacza bez konwersji. Wywołanie jest dozwolone.  
  
 Elementy członkowskie i znajomym w klasie pochodnej `T`, można przekonwertować na wskaźnik do `T` na wskaźnik do prywatnej bezpośredniej klasie bazowej `T`.  
  
## <a name="access-to-virtual-functions"></a>Dostęp do funkcji wirtualnych  
 Kontrola dostępu jest stosowany do [wirtualnego](../cpp/virtual-cpp.md) funkcji jest określana przez typ używany do wywołania funkcji. Przesłanianie deklaracje funkcji nie wpływają na kontroli dostępu dla danego typu. Na przykład:  
  
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
  
 W poprzednim przykładzie, wywołanie funkcji wirtualnej `GetState` za pomocą wskaźnika do typu `VFuncBase` wywołania `VFuncDerived::GetState`, i `GetState` jest traktowany jako publiczne. Jednak podczas wywoływania `GetState` za pomocą wskaźnika do typu `VFuncDerived` jest naruszenie zasad kontroli dostępu, ponieważ `GetState` jest zadeklarowany jako prywatna w klasie `VFuncDerived`.  
  
> [!CAUTION]
>  Funkcja wirtualna `GetState` można wywoływać za pomocą wskaźnika do klasy bazowej `VFuncBase`. Nie oznacza to, że wywołana funkcja jest klasa bazowa wersję tej funkcji.  
  
## <a name="access-control-with-multiple-inheritance"></a>Kontrola dostępu za pomocą wielokrotnego dziedziczenia  
 W lattices dziedziczenia wielokrotnego obejmujących wirtualne klasy bazowe Podaj imię można uzyskać dostęp przez więcej niż jedną ścieżkę. Ponieważ może być stosowana kontroli dostępu w różnych wzdłuż tych różnych ścieżek, kompilator wybiera ścieżką, która pozwala na większości dostępu. Zobacz poniższą ilustrację.  
  
 ![Dostęp wzdłuż ścieżek Wykres dziedziczenia](../cpp/media/vc38v91.gif "vc38V91")  
Dostęp wzdłuż ścieżek Wykres dziedziczenia  
  
 Na rysunku, nazwa zadeklarowana w klasie `VBase` zawsze zostanie osiągnięty za pośrednictwem klasy `RightPath`. Właściwym rozwiązaniem jest bardziej dostępny ponieważ `RightPath` deklaruje `VBase` jako publiczne klasy bazowej, natomiast `LeftPath` deklaruje `VBase` jako prywatny.  
  

## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)
