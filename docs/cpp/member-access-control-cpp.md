---
title: "Kontrola dostępu do elementów członkowskich (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88fe05ab0c0e6a1c433bf2b6007fb63c18fb5850
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="member-access-control-c"></a>Kontrola dostępu do elementów członkowskich (C++)
Kontrolę dostępu umożliwiają oddzielenie [publicznego](../cpp/public-cpp.md) interfejsu klasy z [prywatnej](../cpp/private-cpp.md) szczegóły implementacji i [chronione](../cpp/protected-cpp.md) elementów członkowskich, które są tylko w przypadku użycia przez klasy pochodne. Specyfikator dostępu ma zastosowanie do wszystkich elementów członkowskich zadeklarowanych po nim, dopóki nie napotkano dalej specyfikator dostępu.  
  
```  
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
  
 Dostęp do domyślnej jest `private` w klasie, a `public` w struktury lub związku. Specyfikatory dostępu do klasy mogą być używane w dowolnej kolejności dowolną liczbę razy. Alokacja pamięci dla obiektów typu klasy jest zależy od implementacji, ale elementy członkowskie dotrą do przypisania kolejno adresów pamięci między specyfikatory dostępu.  
  
### <a name="member-access-control"></a>Kontrola dostępu do elementów członkowskich  
  
|Typ dostępu|Znaczenie|  
|--------------------|-------------|  
|[private](../cpp/private-cpp.md)|Elementy członkowskie klasy zadeklarowany jako `private` mogą być używane tylko przez funkcje Członkowskie i znajomych (klasy lub funkcje) klasy.|  
|[protected](../cpp/protected-cpp.md)|Elementy członkowskie klasy zadeklarowany jako `protected` mogą być używane przez funkcje Członkowskie i znajomych (klasy lub funkcje) klasy. Ponadto może być używany przez klasy pochodnej z klasy.|  
|[public](../cpp/public-cpp.md)|Elementy członkowskie klasy zadeklarowany jako **publicznego** może być używana przez funkcję.|  
  
 Kontrola dostępu ułatwia uniemożliwić korzystanie z obiektów w sposób, które nie zostały one przeznaczone do użycia. Ta ochrona jest utracone, gdy są wykonywane jawne konwersje typów (rzutowania).  
  
> [!NOTE]
>  Kontrola dostępu jest stosowane jednakowo do wszystkich nazw: funkcje Członkowskie, element członkowski danych klasy zagnieżdżone i moduły wyliczające.  
  
## <a name="access-control-in-derived-classes"></a>Kontrola dostępu w klasach pochodnych  
 Formant dwa czynniki, które elementy członkowskie klasy podstawowej są dostępne w klasie pochodnej; te czynniki samej kontroli dostępu do dziedziczone elementy członkowskie w klasie pochodnej:  
  
-   Określa, czy klasa pochodna deklaruje przy użyciu klasy podstawowej **publicznego** dostępu specyfikator w *head klasy* (*head klasy* jest opisana w sekcji gramatyki [ Definiowanie typów klasy](http://msdn.microsoft.com/en-us/e8c65425-0f3a-4dca-afc2-418c3b1e57da)).  
  
-   Dostęp do elementu członkowskiego nowości w klasie podstawowej.  
  
 W poniższej tabeli przedstawiono interakcje między te czynniki oraz sposobu określania dostępu do elementu członkowskiego klasy podstawowej.  
  
### <a name="member-access-in-base-class"></a>Dostęp do elementu członkowskiego w klasie podstawowej  
  
|private|protected|Public|  
|-------------|---------------|------------|  
|Zawsze niedostępny, niezależnie od dostępu wyprowadzenia|Prywatny w klasie pochodnej, jeśli używasz pochodnym prywatnej|Prywatny w klasie pochodnej, jeśli używasz pochodnym prywatnej|  
||Chronione w klasie pochodnej, jeśli używasz chronionych wyprowadzenia|Chronione w klasie pochodnej, jeśli używasz chronionych wyprowadzenia|  
||Chronione w klasie pochodnej, jeśli używasz publicznego wyprowadzenia|W klasie pochodnej, jeśli używasz publicznego pochodnym publiczny|  
  
 Poniższy przykład przedstawia to:  
  
```  
// access_specifiers_for_base_classes.cpp  
class BaseClass  
{  
public:  
    int PublicFunc();    // Declare a public member.  
protected:  
    int ProtectedFunc(); // Declare a protected member.  
private:  
    int PrivateFunc();   // Declare a private member.  
};  
  
// Declare two classes derived from BaseClass.  
class DerivedClass1 : public BaseClass  
{  
};  
  
class DerivedClass2 : private BaseClass  
{  
};  
  
int main()  
{  
}  
```  
  
 W `DerivedClass1`, funkcja członkowska `PublicFunc` jest publicznym elementem członkowskim i `ProtectedFunc` jest chroniony element członkowski, ponieważ `BaseClass` jest klasą podstawową publicznego. `PrivateFunc`jest oznaczony jako prywatny `BaseClass`, i jest niedostępny dla dowolnej klasy pochodnej.  
  
 W `DerivedClass2`, funkcje `PublicFunc` i `ProtectedFunc` są uznawane za prywatne elementy członkowskie, ponieważ `BaseClass` jest klasą podstawową prywatnych. Ponownie `PrivateFunc` jest prywatnym kodem `BaseClass`, i jest niedostępny dla dowolnej klasy pochodnej.  
  
 Można zadeklarować klasy pochodnej bez specyfikatora dostępu do klasy podstawowej. W takim przypadku informacje o pochodzeniu jest uznawane za prywatne, jeśli używa deklaracji klasy pochodnej **klasy** — słowo kluczowe. Informacje o pochodzeniu jest uznawany za publiczne, jeśli używa deklaracji klasy pochodnej `struct` — słowo kluczowe. Na przykład następujący kod:  
  
```  
class Derived : Base  
...  
```  
  
 odpowiada to:  
  
```  
class Derived : private Base  
...  
```  
  
 W podobny sposób następujący kod:  
  
```  
struct Derived : Base  
...  
```  
  
 odpowiada to:  
  
```  
struct Derived : public Base  
...  
```  
  
 Należy pamiętać, że elementów członkowskich zadeklarowanych jako prywatnych dostępu nie są dostępne dla funkcji lub klas pochodnych, chyba że te funkcje lub klasy zadeklarowane za pomocą `friend` deklaracji w klasie podstawowej.  
  
 A **Unii** typ nie może mieć klasy podstawowej.  
  
> [!NOTE]
>  Podczas określania prywatnych klasy podstawowej, zaleca się jawnie używać `private` — słowo kluczowe, dlatego użytkownicy klasy pochodnej zrozumieć dostęp do elementu członkowskiego.  
  
## <a name="access-control-and-static-members"></a>Kontrola dostępu i statyczne składniki  
 Po określeniu klasy podstawowej jako `private`, ma wpływ tylko Niestatyczne elementy członkowskie. Publiczne statyczne elementy członkowskie są nadal dostępne w klasach pochodnych. Jednak podczas uzyskiwania dostępu do elementów członkowskich klasy podstawowej za pomocą obiektów, odwołania lub wskaźniki może wymagać konwersji, które ponownie zastosować kontroli dostępu. Rozważmy następujący przykład:  
  
```  
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
  
 W powyższym kodzie kontroli dostępu zabrania konwersja ze wskaźnika do `Derived2` na wskaźnik do `Base`. **To** wskaźnika jest niejawnie typu `Derived2 *`. Aby wybrać `CountOf` funkcji **to** musi zostać przekonwertowana na typ `Base *`. Takie konwersja nie jest dozwolona, ponieważ `Base` jest prywatny pośredniej klasy podstawowej do `Derived2`. Konwersja na typ klasy podstawowej prywatnej jest dopuszczalne tylko dla wskaźników do natychmiastowego klas pochodnych. W związku z tym wskaźników typu `Derived1 *` można przekonwertować na typ `Base *`.  
  
 Należy pamiętać, że wywołania `CountOf` funkcja jawnie, bez użycia wskaźnika, reference lub obiektu, wybierz ją, oznacza brak konwersji. Wywołanie jest dozwolone.  
  
 Elementy członkowskie i znajomych w klasie pochodnej `T`, można przekonwertować wskaźnika do `T` na wskaźnik do prywatnego bezpośredniej klasie podstawowej z `T`.  
  
## <a name="access-to-virtual-functions"></a>Dostęp do funkcji wirtualnych  
 Kontrola dostępu jest stosowany do [wirtualnego](../cpp/virtual-cpp.md) funkcji jest określana przez typ używane do tworzenia wywołań funkcji. Zastępowanie deklaracje funkcji nie wpływają na kontroli dostępu dla danego typu. Na przykład:  
  
```  
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
  
 W poprzednim przykładzie, wywołanie funkcji wirtualnej `GetState` przy użyciu wskaźnika do typu `VFuncBase` wywołania `VFuncDerived::GetState`, i `GetState` jest traktowane jako publiczne. Jednak podczas wywoływania `GetState` przy użyciu wskaźnika do typu `VFuncDerived` jest naruszenie zasad kontroli dostępu, ponieważ `GetState` jest zadeklarowany jako prywatny w klasie `VFuncDerived`.  
  
> [!CAUTION]
>  Funkcji wirtualnej `GetState` można wywołać przy użyciu wskaźnika do klasy podstawowej `VFuncBase`. Oznacza to, że funkcja wywoływana jest w wersji klasy podstawowej w tej funkcji.  
  
## <a name="access-control-with-multiple-inheritance"></a>Kontrola dostępu przy użyciu dziedziczenie wielokrotne  
 W lattices dziedziczenia wielokrotnego obejmujących wirtualne klasy podstawowe podanej nazwie jest osiągalna przez więcej niż jedną ścieżkę. Ponieważ kontroli dostępu różnych można zastosować wzdłuż ścieżki te różne ścieżki, która zapewnia dostęp większości wybierze kompilator. Zobacz poniższą ilustrację.  
  
 ![Dostęp wzdłuż ścieżki Wykres dziedziczenia](../cpp/media/vc38v91.gif "vc38V91")  
Dostęp wzdłuż ścieżki Wykres dziedziczenia  
  
 Na rysunku nazwę zadeklarowana w klasie `VBase` zawsze osiągnięciu za pośrednictwem klasy `RightPath`. Właściwym rozwiązaniem jest bardziej dostępny ponieważ `RightPath` deklaruje `VBase` jako klasę podstawową publiczne, podczas gdy `LeftPath` deklaruje `VBase` jako prywatny.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)