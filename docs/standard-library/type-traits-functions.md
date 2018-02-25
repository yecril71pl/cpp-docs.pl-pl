---
title: '&lt;type_traits&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
- type_traits/std::is_copy_assignable
- type_traits/std::is_copy_constructible
- type_traits/std::is_default_constructible
- type_traits/std::is_move_assignable
- type_traits/std::is_move_constructible
- type_traits/std::is_nothrow_move_assignable
- type_traits/std::is_trivially_copy_assignable
- type_traits/std::is_trivially_move_assignable
- type_traits/std::is_trivially_move_constructible
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: 67fd80381854bd141fd47314544aca745f9a9aaf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="lttypetraitsgt-functions"></a>&lt;type_traits&gt; funkcji
||||  
|-|-|-|  
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|  
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|  
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|[is_trivially_move_assignable](#is_trivially_move_assignable)|  
|[is_trivially_move_constructible](#is_trivially_move_constructible)|  
  
##  <a name="is_assignable"></a>  is_assignable  
 Sprawdza, czy wartość `From` typu mogą być przypisane do `To` typu.  
  
```  
template <class To, class From>  
struct is_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 Do  
 Typ obiektu, który odbiera przypisania.  
  
 Z  
 Typ obiektu, który zawiera wartość.  
  
### <a name="remarks"></a>Uwagi  
 Wyrażenie, którego nie obliczono `declval<To>() = declval<From>()` musi być poprawnie sformułowany. Zarówno `From` i `To` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.  
  
##  <a name="is_copy_assignable"></a>  is_copy_assignable  
 Testy czy typ ma można kopiować przypisania.  
  
```  
template <class Ty>  
struct is_copy_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
### <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest klasa, która ma operatora przypisania kopii, w przeciwnym razie posiada wartość false. Odpowiednikiem is_assignable\<Ty & const Ty & >.  
  
##  <a name="is_copy_constructible"></a>  is_copy_constructible  
 Testy, jeśli typ ma konstruktora kopiującego.  
  
```  
template <class Ty>  
struct is_copy_constructible;  
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
### <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest klasa, która ma konstruktora kopiującego, w przeciwnym razie posiada wartość false.  
  
### <a name="example"></a>Przykład  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
struct Copyable  
{  
    int val;  
};  
  
struct NotCopyable  
{  
   NotCopyable(const NotCopyable&) = delete;  
   int val;  
  
};  
  
int main()  
{  
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha  
        << std::is_copy_constructible<Copyable>::value << std::endl;  
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha  
        << std::is_copy_constructible<NotCopyable>::value << std::endl;  
  
    return (0);  
}  
  
```  
  
```Output  
is_copy_constructible<Copyable> == true  
is_copy_constructible<NotCopyable > == false  
```  
  
##  <a name="is_default_constructible"></a>  is_default_constructible  
 Testy, jeśli typ ma konstruktora domyślnego.  
  
```  
template <class Ty>  
struct is_default_constructible;  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
### <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest typem klasy, który ma domyślny konstruktor, w przeciwnym razie posiada wartość false. Jest to równoważne predykatu `is_constructible<T>`. Typ `T` musi być typem pełną `void`, lub tablicy z nieznanym powiązaniem.  
  
### <a name="example"></a>Przykład  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
struct Simple  
{  
    Simple() : val(0) {}  
    int val;  
};  
  
struct Simple2  
{  
    Simple2(int v) : val(v) {}  
    int val;  
};  
  
int main()  
{  
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha  
        << std::is_default_constructible<Simple>::value << std::endl;  
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha  
        << std::is_default_constructible<Simple2>::value << std::endl;  
  
    return (0);  
}  
  
```  
  
```Output  
is_default_constructible<Simple> == true  
is_default_constructible<Simple2> == false  
```  
  
##  <a name="is_move_assignable"></a>  is_move_assignable  
 Testy, jeśli typ można przenieść przypisane.  
  
```  
template <class T>  
struct is_move_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
### <a name="remarks"></a>Uwagi  
 Typ jest przeniesienie można przypisać, jeśli odwołania do r-wartości na typ można przypisać do odwołania do typu. Predykat typów jest odpowiednikiem `is_assignable<T&, T&&>`. Przenieś można przypisać typy referenceable typów skalarnych i operatory przypisania przenoszenia typy klas, którzy generowane przez kompilator lub zdefiniowanej przez użytkownika.  
  
##  <a name="is_move_constructible"></a>  is_move_constructible  
 Sprawdza, czy typ ma konstruktora przenoszenia.  
  
```  
template <class T>  
struct is_move_constructible;  
```  
  
### <a name="parameters"></a>Parametry  
 T  
 Typ, który ma zostać obliczone  
  
### <a name="remarks"></a>Uwagi  
 Predykat typów, która daje w wyniku wartość true, jeśli typ `T` może być skonstruowany przy użyciu operacji przenoszenia. Odpowiada to predykatu `is_constructible<T, T&&>`.  
  
##  <a name="is_nothrow_move_assignable"></a>  is_nothrow_move_assignable  
 Sprawdza, czy typ ma **nothrow** przenoszący operator przypisania.  
  
```  
template <class Ty>  
struct is_nothrow_move_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
### <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` ma nothrow operator przypisania przenoszenia, w przeciwnym razie posiada wartość false.  
  
##  <a name="is_trivially_copy_assignable"></a>  is_trivially_copy_assignable  
 Sprawdza, czy typ ma operatora przypisania kopii prosta.  
  
```  
template <class Ty>  
struct is_trivially_copy_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
### <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest klasa, która ma trivial operatora przypisania kopii, w przeciwnym razie posiada wartość false.  
  
 Konstruktor przypisania dla klasy `T` jest proste, jeśli jest niejawnie podany, klasa `T` ma żadnych funkcji wirtualnych klasy `T` ma nie wirtualnych typów podstawowych, klas wszystkich członków danych niestatycznych typu klasy mają prosta Operatory przypisania i klasy wszystkich członków danych niestatycznych tablicy typu klasy mają operatory przypisania prosta.  
  
##  <a name="is_trivially_move_assignable"></a>  is_trivially_move_assignable  
 Sprawdza, czy typ ma operator przypisania przenoszenia prosta.  
  
```  
template <class Ty>  
struct is_trivially_move_assignable;  
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
### <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest klasa, która ma trivial operator przypisania przenoszenia, w przeciwnym razie posiada wartość false.  
  
 Operator przypisania przenoszenia, dla klasy `Ty` jest prosta jeśli:  
  
 niejawnie podano  
  
 Klasa `Ty` ma żadnych funkcji wirtualnych  
  
 Klasa `Ty` ma nie wirtualnych typów podstawowych  
  
 klasy wszystkich członków danych niestatycznych typu klasy mają trivial przenoszące operatory przypisania  
  
 klasy wszystkich członków danych niestatycznych tablicy typu klasy mają trivial przenoszące operatory przypisania  
  
##  <a name="is_trivially_move_constructible"></a>  is_trivially_move_constructible  
 Testy, jeśli typ ma trivial przenoszenie konstruktora.  
  
```  
template <class Ty>  
struct is_trivially_move_constructible;  
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
### <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest klasa, która ma Konstruktor przenoszący trivial w inny sposób przechowuje wartość false.  
  
 Przenoszenie konstruktora dla klasy `Ty` jest prosta jeśli:  
  
 został niejawnie zadeklarowany.  
  
 jego typy parametrów są odpowiadające niejawne deklaracji  
  
 Klasa `Ty` ma żadnych funkcji wirtualnych  
  
 Klasa `Ty` ma nie wirtualnych typów podstawowych  
  
 Klasa nie ma żadnych członków danych niestatycznych nietrwałe  
  
 wszystkie bezpośrednio podstawowych klasy `Ty` mieć konstruktorów przenoszenia prosta  
  
 klasy wszystkich członków danych niestatycznych typu klasy mają konstruktorów przenoszenia prosta  
  
 klasy wszystkich członków danych niestatycznych tablicy typu klasy mają konstruktorów przenoszenia prosta  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)

