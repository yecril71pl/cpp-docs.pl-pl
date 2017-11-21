---
title: "scoped_allocator_adaptor — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
dev_langs: C++
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c74216b8b510b17327c22a087295725049c4f024
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor — klasa
Reprezentuje gniazdo allocators —.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <class Outer, class... Inner>  
class scoped_allocator_adaptor;  
```  
  
## <a name="remarks"></a>Uwagi  
 Klasy szablonów hermetyzuje gniazdo allocators — jeden lub więcej. Każda takie klasa ma peryferyjnych alokatora typu `outer_allocator_type`, synonimem `Outer`, który jest publiczny podstawą `scoped_allocator_adaptor` obiektu. `Outer`Służy do przydzielenia pamięci, który będzie używany przez kontener. Odwołanie do tego obiektu podstawowego alokatora można uzyskać przez wywołanie metody `outer_allocator`.  
  
 W pozostałej części zestawu ma typ `inner_allocator_type`. Wewnętrzny program przydzielania służy można przydzielić pamięci dla elementów w kontenerze. Odwołanie do składowanej obiektu tego typu można uzyskać przez wywołanie metody `inner_allocator`. Jeśli `Inner...` nie jest pusta, `inner_allocator_type` ma typ `scoped_allocator_adaptor<Inner...>`, i `inner_allocator` wyznacza obiektu elementu członkowskiego. W przeciwnym razie `inner_allocator_type` ma typ `scoped_allocator_adaptor<Outer>`, i `inner_allocator` wyznacza całego obiektu.  
  
 Zestawu zachowuje się tak, jakby składa się z dowolnego głębię replikowanie jego najbardziej alokatora hermetyzowany zgodnie z potrzebami.  
  
 Kilka pojęć, które nie są częścią widoczne interfejsu pomocy w opisujący zachowanie tej klasy szablonu. *Peryferyjnych alokatora* przekazuje wszystkie wywołania konstrukcja i zniszcz metody. Efektywne jest definiowana za pomocą funkcji recursive `OUTERMOST(X)`, gdzie `OUTERMOST(X)` jest jednym z następujących czynności.  
  
-   Jeśli `X.outer_allocator()` jest poprawnie sformułowany, następnie `OUTERMOST(X)` jest `OUTERMOST(X.outer_allocator())`.  
  
-   W przeciwnym razie `OUTERMOST(X)` jest `X`.  
  
 Trzy typy są definiowane dla specyfikacji:  
  
|Typ|Opis|  
|----------|-----------------|  
|`Outermost`|Typ `OUTERMOST(*this)`.|  
|`Outermost_traits`|`allocator_traits<Outermost>`|  
|`Outer_traits`|`allocator_traits<Outer>`|  
  
### <a name="constructors"></a>Konstruktorów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[scoped_allocator_adaptor —](#scoped_allocator_adaptor)|Konstruuje `scoped_allocator_adaptor` obiektu.|  
  
### <a name="typedefs"></a>Typedefs  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`const_pointer`|Ten typ jest synonimem `const_pointer` skojarzonego z programu przydzielania `Outer`.|  
|`const_void_pointer`|Ten typ jest synonimem `const_void_pointer` skojarzonego z programu przydzielania `Outer`.|  
|`difference_type`|Ten typ jest synonimem `difference_type` skojarzonego z programu przydzielania `Outer`.|  
|`inner_allocator_type`|Ten typ jest synonim dla typu zagnieżdżonego karty `scoped_allocator_adaptor<Inner...>`.|  
|`outer_allocator_type`|Ten typ jest synonim dla typu podstawowego alokatora `Outer`.|  
|`pointer`|Ten typ jest synonimem `pointer` skojarzone z programu przydzielania `Outer`.|  
|`propagate_on_container_copy_assignment`|Typ ma wartość true tylko wtedy, gdy `Outer_traits::propagate_on_container_copy_assignment` prawdziwe lub `inner_allocator_type::propagate_on_container_copy_assignment` jest spełniony.|  
|`propagate_on_container_move_assignment`|Typ ma wartość true tylko wtedy, gdy `Outer_traits::propagate_on_container_move_assignment` prawdziwe lub `inner_allocator_type::propagate_on_container_move_assignment` jest spełniony.|  
|`propagate_on_container_swap`|Typ ma wartość true tylko wtedy, gdy `Outer_traits::propagate_on_container_swap` prawdziwe lub `inner_allocator_type::propagate_on_container_swap` jest spełniony.|  
|`size_type`|Ten typ jest synonimem `size_type` skojarzone z programu przydzielania `Outer`.|  
|`value_type`|Ten typ jest synonimem `value_type` skojarzone z programu przydzielania `Outer`.|  
|`void_pointer`|Ten typ jest synonimem `void_pointer` skojarzone z programu przydzielania `Outer`.|  
  
### <a name="structs"></a>Struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[scoped_allocator_adaptor::rebind — struktura](#rebind_struct)|Definiuje typ `Outer::rebind\<Other>::other` jako synonimem `scoped_allocator_adaptor\<Other, Inner...>`.|  
  
### <a name="methods"></a>Metody  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Przydziel](#allocate)|Przydziela pamięć przy użyciu `Outer` przydzielania.|  
|[konstrukcja](#construct)|Tworzy obiekt.|  
|[cofnięcie przydziału](#deallocate)|Cofa alokację obiektów, używając programu przydzielania zewnętrzne.|  
|[Destroy](#destroy)|Niszczy określonego obiektu.|  
|[inner_allocator](#inner_allocator)|Pobiera odwołanie do obiektu przechowywanych typu `inner_allocator_type`.|  
|[max_size](#max_size)|Określa maksymalną liczbę obiektów, które mogą zostać przydzieleni przez zewnętrzne przydzielania.|  
|[outer_allocator](#outer_allocator)|Pobiera odwołanie do obiektu przechowywanych typu `outer_allocator_type`.|  
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Tworzy nowy `scoped_allocator_adaptor` obiektu z każdego obiektu przechowywanych alokatora inicjowany przez wywołanie `select_on_container_copy_construction` dla każdego odpowiedniego przydzielania.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<scoped_allocator >  
  
 **Namespace:** Standard  
  
##  <a name="allocate"></a>scoped_allocator_adaptor::allocate
 Przydziela pamięć przy użyciu `Outer` przydzielania.  
  
```cpp  
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Liczba elementów, dla których ma zostać przydzielone wystarczającej ilości miejsca.  
  
 `hint`  
 Wskaźnik, która może ułatwić obiektu alokatora dzięki umieszczeniu adres obiektu przydzielone przed żądania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwszy funkcji członkowskiej `Outer_traits::allocate(outer_allocator(), count)`. Zwraca drugie funkcji członkowskiej `Outer_traits::allocate(outer_allocator(), count, hint)`.  
  
##  <a name="construct"></a>scoped_allocator_adaptor::Construct
 Tworzy obiekt.  
  
```cpp  
template <class Ty, class... Atypes>  
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>  
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,  
    tuple<Atypes1&&...>  
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>  
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr,  
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Wskaźnik do lokalizacji pamięci, której obiekt ma być skonstruowany.  
  
 `args`  
 Lista argumentów.  
  
 `first`  
 Obiekt pierwszego typu w parze.  
  
 `second`  
 Obiekt typu Druga para.  
  
 `right`  
 Istniejący obiekt przenoszone lub kopiowane.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsza metoda tworzy obiekt w `ptr` przez wywołanie metody `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, gdzie `xargs...` jest jednym z następujących czynności.  
  
-   Jeśli `uses_allocator<Ty, inner_allocator_type>` ma wartość false, następnie `xargs...` jest `args...`.  
  
-   Jeśli `uses_allocator<Ty, inner_allocator_type>` jest spełniony, a `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` jest spełniony, następnie `xargs...` jest `allocator_arg, inner_allocator(), args...`.  
  
-   Jeśli `uses_allocator<Ty, inner_allocator_type>` jest spełniony, a `is_constructible<Ty, args..., inner_allocator()>` jest spełniony, następnie `xargs...` jest `args..., inner_allocator()`.  
  
 Druga metoda tworzy obiekt pary pod `ptr` przez wywołanie metody `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`, gdzie `xargs...` jest `first...` zmodyfikowane tak jak na powyższej liście, i `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, gdzie `xargs...` jest `second...` zmodyfikowane w powyższej listy.  
  
 Trzeci — metoda działa tak samo jak `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.  
  
 Czwarty — metoda działa tak samo jak `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.  
  
 Piąty — metoda działa tak samo jak `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.  
  
 Szóstego metody działa tak samo jak `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.  
  
##  <a name="deallocate"></a>scoped_allocator_adaptor::deallocate
 Cofa alokację obiektów, używając programu przydzielania zewnętrzne.  
  
```cpp  
void deallocate(pointer ptr, size_type count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Wskaźnik do lokalizacji początkowej obiektów do przydzielenia.  
  
 `count`  
 Liczba obiektów można cofnąć alokacji.  
  
##  <a name="destroy"></a>scoped_allocator_adaptor::Destroy
 Niszczy określonego obiektu.  
  
```cpp  
template <class Ty>  
void destroy(Ty* ptr)  
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Wskaźnik do obiektu, które mają zostać zniszczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 `Outermost_traits::destroy(OUTERMOST(*this), ptr)`  
  
##  <a name="inner_allocator"></a>scoped_allocator_adaptor::inner_allocator
 Pobiera odwołanie do obiektu przechowywanych typu `inner_allocator_type`.  
  
```cpp  
inner_allocator_type& inner_allocator() noexcept;  
const inner_allocator_type& inner_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu przechowywanych typu `inner_allocator_type`.  
  
##  <a name="max_size"></a>scoped_allocator_adaptor::max_size
 Określa maksymalną liczbę obiektów, które mogą zostać przydzieleni przez zewnętrzne przydzielania.  
  
```cpp  
size_type max_size();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `Outer_traits::max_size(outer_allocator())`  
  
##  <a name="outer_allocator"></a>scoped_allocator_adaptor::outer_allocator
 Pobiera odwołanie do obiektu przechowywanych typu `outer_allocator_type`.  
  
```cpp  
outer_allocator_type& outer_allocator() noexcept;  
const outer_allocator_type& outer_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu przechowywanych typu `outer_allocator_type`.  
  
##  <a name="rebind_struct"></a>scoped_allocator_adaptor::rebind — struktura  
 Definiuje typ `Outer::rebind\<Other>::other` jako synonimem `scoped_allocator_adaptor\<Other, Inner...>`.  
  
{ponowne wiązanie — struktura  
   Element TypeDef Other_traits::rebind\<innych >  
   Other_alloc;  
   scoped_allocator_adaptor — TypeDef\<Other_alloc, wewnętrzny... > innych;  
   };  
  
##  <a name="scoped_allocator_adaptor"></a>scoped_allocator_adaptor::scoped_allocator_adaptor — Konstruktor  
 Konstruuje `scoped_allocator_adaptor` obiektu.  
  
```cpp  
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(Outer2&& al,  
    const Inner&... rest) noexcept;  
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Istniejące `scoped_allocator_adaptor`.  
  
 `al`  
 Istniejące alokatora ma być używany jako zewnętrzne przydzielania.  
  
 `rest`  
 Lista allocators — ma być używany jako wewnętrzny allocators —.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy domyślnego konstruktora tworzy alokatora przechowywanych przez nią obiektów. Konstruuje każdego z trzech kolejnych konstruktorów jego obiektów przechowywanych alokatora z odpowiednimi obiektami w `right`. Ostatni konstruktora tworzy jej obiektów przechowywanych alokatora z odpowiedniego argumentów listy argumentów.  
  
##  <a name="select_on_container_copy_construction"></a>scoped_allocator_adaptor::select_on_container_copy_construction
 Tworzy nowy `scoped_allocator_adaptor` obiektu z każdego obiektu przechowywanych alokatora inicjowany przez wywołanie `select_on_container_copy_construction` dla każdego odpowiedniego przydzielania.  
  
```cpp  
scoped_allocator_adaptor select_on_container_copy_construction();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwróci wartość skutecznie `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. Wynik jest nowy `scoped_allocator_adaptor` obiektu z każdego obiektu przechowywanych alokatora inicjowany przez wywołanie `al.select_on_container_copy_construction()` dla odpowiedniego alokatora `al`.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)



