---
title: "weak_ptr — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
dev_langs: C++
helpviewer_keywords:
- std::weak_ptr [C++]
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: db0ab662735a29e1b37536ebbccf3e94fa056070
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="weakptr-class"></a>weak_ptr — Klasa
Otacza słabo połączony wskaźnik.  
  
## <a name="syntax"></a>Składnia  
```    
template<class _Ty>
   class weak_ptr {  
public:  
   typedef Ty element_type;  
   weak_ptr();
   weak_ptr(const weak_ptr&);
   template <class Other>  
      weak_ptr(const weak_ptr<Other>&);
   template <class Other>  
      weak_ptr(const shared_ptr<Other>&);
   weak_ptr& operator=(const weak_ptr&);
   template <class Other>  
      weak_ptr& operator=(const weak_ptr<Other>&);
   template <class Other>  
      weak_ptr& operator=(shared_ptr<Other>&);
   void swap(weak_ptr&);
   void reset();
   long use_count() const;
   bool expired() const;
   shared_ptr<Ty> lock() const;
   };  
```    
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ kontrolowane przez słabe wskaźnika.  
  
## <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje obiekt, który wskazuje z zasobem, który jest zarządzany przez jedną lub więcej [shared_ptr — klasa](../standard-library/shared-ptr-class.md) obiektów. `weak_ptr` Obiektów, które wskazują na zasób nie ma wpływu na liczbę odwołań zasobu. W związku z tym, kiedy ostatniego `shared_ptr` obiektu, który zarządza tego zasobu zasób zostanie zwolniona, nawet jeśli istnieją `weak_ptr` obiektów wskazanie do tego zasobu. Jest to konieczne do uniknięcia cykle w strukturach danych.  
  
 A `weak_ptr` obiektu punktów do zasobu, jeśli został skonstruowany z `shared_ptr` obiektu będącego właścicielem tego zasobu, jeśli został skonstruowany z `weak_ptr` obiekt, który wskazuje tego zasobu lub jeśli ten zasób został przypisany do niego z [ operator =](#op_eq). A `weak_ptr` obiektu nie zapewnia bezpośredni dostęp do zasobu, który wskazuje. Kod, który musi korzystać z zasobów jest więc za pomocą `shared_ptr` obiektu, który jest właścicielem tego zasobu, utworzona przez wywołanie funkcji Członkowskich [blokady](#lock). A `weak_ptr` obiektu wygasła, gdy zasób, który wskazuje został zwolniony, ponieważ wszystkie `shared_ptr` zostały zniszczone obiektów, których właścicielem zasobu. Wywoływanie `lock` na `weak_ptr` obiektu, który wygasł tworzy obiekt shared_ptr puste.  
  
 Weak_ptr — pusty obiekt nie wskazuje żadnych zasobów i ma nie bloku sterowania. Jego funkcji członkowskiej `lock` zwraca obiekt shared_ptr puste.  
  
 Cykl występuje, gdy dwie lub więcej zasobów kontrolowane przez `shared_ptr` przechowywania obiektów wzajemnie odwołujące się do `shared_ptr` obiektów. Na przykład cykliczne listy połączonej z trzech elementów ma węzła głównego `N0`; ten węzeł zawiera `shared_ptr` obiektu, który jest właścicielem następnego węzła `N1`; ten węzeł zawiera `shared_ptr` obiektu, który jest właścicielem następnego węzła `N2`; tego węzła, w Włącz blokad `shared_ptr` obiektu, który jest właścicielem węzła głównego `N0`, zamykanie cyklu. W takiej sytuacji brak liczby odwołań kiedykolwiek staną się zero, a węzły w cyklu nie zostanie zwolniona. Aby wyeliminować cykl, ostatni węzeł `N2` powinno zawierać `weak_ptr` obiekt wskazujący `N0` zamiast `shared_ptr` obiektu. Ponieważ `weak_ptr` nie jest właścicielem obiektu `N0` nie wpływa na `N0`przez odwołanie liczby i gdy ostatnie odwołanie programu z węzłem głównym zostanie zniszczony węzły na liście również zostaną usunięte.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[weak_ptr —](#weak_ptr)|Konstruuje `weak_ptr`.|  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[ELEMENT_TYPE](#element_type)|Typ elementu.|  
|[ważność](#expired)|Testy, jeśli prawo własności wygasło.|  
|[blokady](#lock)|Uzyskuje wyłącznego prawa własności do zasobu.|  
|[owner_before](#owner_before)|Zwraca `true` Jeśli `weak_ptr` jest umieszczane przed (lub mniej niż) podany wskaźnik.|  
|[Resetowanie](#reset)|Wersje właściciela zasobów.|  
|[swap](#swap)|Zamienia dwa `weak_ptr` obiektów.|  
|[use_count](#use_count)|Wyznaczony numer liczby `shared_ptr` obiektów.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#op_eq)|Zamienia właściciela zasobów.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<pamięci >  
  
 **Namespace:** Standard  
  
##  <a name="element_type"></a>ELEMENT_TYPE  
 Typ elementu.  
  
```  
typedef Ty element_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Ty`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__memory__weak_ptr_element_type.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::shared_ptr<int> sp0(new int(5));   
    std::weak_ptr<int> wp0(sp0);   
    std::weak_ptr<int>::element_type val = *wp0.lock();   
  
    std::cout << "*wp0.lock() == " << val << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
*wp0.lock() == 5  
```  
  
##  <a name="expired"></a>ważność  
 Testy, jeśli prawo własności wygasło.  
  
```  
bool expired() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca `true` Jeśli `*this` wygasł, w przeciwnym razie `false`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__memory__weak_ptr_expired.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed   
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
  
```  
  
```Output  
wp.expired() == false  
*wp.lock() == 10  
wp.expired() == true  
(bool)wp.lock() == false  
```  
  
##  <a name="lock"></a>blokady  
 Uzyskuje wyłącznego prawa własności do zasobu.  
  
```  
shared_ptr<Ty> lock() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca obiekt shared_ptr pusty, jeśli `*this` wygasła; w przeciwnym razie zwraca [shared_ptr — klasa](../standard-library/shared-ptr-class.md) `<Ty>` obiekt, który jest właścicielem zasobu `*this` wskazuje.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__memory__weak_ptr_lock.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed   
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
  
```  
  
```Output  
wp.expired() == false  
*wp.lock() == 10  
wp.expired() == true  
(bool)wp.lock() == false  
```  
  
##  <a name="op_eq"></a>operator =  
 Zamienia właściciela zasobów.  
  
```  
weak_ptr& operator=(const weak_ptr& wp);

template <class Other>  
weak_ptr& operator=(const weak_ptr<Other>& wp);

template <class Other>  
weak_ptr& operator=(const shared_ptr<Other>& sp);
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 Typ kontrolowane przez wskaźnik udostępnionych niska argumentu.  
  
 `wp`  
 Słabe wskaźnik do skopiowania.  
  
 `sp`  
 Udostępniony wskaźnik do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie operatory zwolnienia zasobu wskazywana aktualnie przez `*this` i Przypisz własność zasobów o nazwie sekwencja operand `*this`. Jeśli operator nie pozostawia `*this` bez zmian.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__memory__weak_ptr_operator_as.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::shared_ptr<int> sp1(new int(10));
    wp0 = sp1;
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::weak_ptr<int> wp1;
    wp1 = wp0;
    std::cout << "*wp1.lock() == " << *wp1.lock() << std::endl;

    return (0);
}
  
```  
  
```Output  
*wp0.lock() == 5  
*wp0.lock() == 10  
*wp1.lock() == 10  
```  
  
##  <a name="owner_before"></a>owner_before  
 Zwraca `true` Jeśli `weak_ptr` jest umieszczane przed (lub mniej niż) podany wskaźnik.  
  
```  
template <class Other>  
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>  
bool owner_before(const weak_ptr<Other>& ptr);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 `lvalue` Odwołania do albo `shared_ptr` lub `weak_ptr`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca funkcję elementu członkowskiego szablonu `true` Jeśli `*this` jest `ordered before` `ptr`.  
  
##  <a name="reset"></a>Resetowanie  
 Wersje właściciela zasobów.  
  
```  
void reset();
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwalnia zasobu wskazywanego przez `*this` i konwertuje `*this` do obiektu weak_ptr puste.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__memory__weak_ptr_reset.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp(new int(5));
    std::weak_ptr<int> wp(sp);
    std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    wp.reset();
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    return (0);
}

```  
  
```Output  
*wp.lock() == 5  
wp.expired() == false  
wp.expired() == true  
```  
  
##  <a name="swap"></a>swap  
 Zamienia dwa `weak_ptr` obiektów.  
  
```  
void swap(weak_ptr& wp);
```  
  
### <a name="parameters"></a>Parametry  
 `wp`  
 Słabe wskaźnik do wymiany.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska pozostawia zasobu pierwotnie wskazywanej przez `*this` następnie wskazywana przez `wp`i zasobu pierwotnie wskazywana przez `wp` następnie wskazywanej przez `*this`. Funkcja nie ulega zmianie liczby odwołań zasobów i generują żadnych wyjątków.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__memory__weak_ptr_swap.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
 
struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}

```  
  
```Output  
*sp1 == 5  
*sp1 == 10  
*sp1 == 5  
  
*wp1 == 5  
*wp1 == 10  
*wp1 == 5  
```  
  
##  <a name="use_count"></a>use_count  
 Wyznaczony numer liczby `shared_ptr` obiektów.  
  
```  
long use_count() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca liczbę `shared_ptr` obiektów, których właścicielem zasobu wskazywanego przez `*this`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__memory__weak_ptr_use_count.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    return (0);
} 
  
```  
  
```Output  
wp.use_count() == 1  
wp.use_count() == 2  
```  
  
##  <a name="weak_ptr"></a>weak_ptr —  
 Konstruuje `weak_ptr`.  
  
```  
weak_ptr();

weak_ptr(const weak_ptr& wp);

template <class Other>  
weak_ptr(const weak_ptr<Other>& wp);

template <class Other>  
weak_ptr(const shared_ptr<Other>& sp);
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 Typ kontrolowane przez wskaźnik udostępnionych niska argumentu.  
  
 `wp`  
 Słabe wskaźnik do skopiowania.  
  
 `sp`  
 Udostępniony wskaźnik do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktory każdego utworzenia obiektu wskazujące zasobów o nazwie przez argument sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__memory__weak_ptr_construct.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::weak_ptr<int> wp0;
    std::cout << "wp0.expired() == " << std::boolalpha
        << wp0.expired() << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp1(sp1);
    std::cout << "*wp1.lock() == "
        << *wp1.lock() << std::endl;

    std::weak_ptr<int> wp2(wp1);
    std::cout << "*wp2.lock() == "
        << *wp2.lock() << std::endl;

    return (0);
}
  
```  
  
```Output  
wp0.expired() == true  
*wp1.lock() == 5  
*wp2.lock() == 5  
```  
  
## <a name="see-also"></a>Zobacz też  
 [shared_ptr — klasa](../standard-library/shared-ptr-class.md)

