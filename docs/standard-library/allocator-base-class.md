---
title: "allocator_base — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_base
- allocators/stdext::allocators::allocator_base
- allocators/stdext::allocator_base::const_pointer
- allocators/stdext::allocator_base::const_reference
- allocators/stdext::allocator_base::difference_type
- allocators/stdext::allocator_base::pointer
- allocators/stdext::allocator_base::reference
- allocators/stdext::allocator_base::size_type
- allocators/stdext::allocator_base::value_type
- allocators/stdext::allocator_base::_Charalloc
- allocators/stdext::allocator_base::_Chardealloc
- allocators/stdext::allocator_base::address
- allocators/stdext::allocator_base::allocate
- allocators/stdext::allocator_base::construct
- allocators/stdext::allocator_base::deallocate
- allocators/stdext::allocator_base::destroy
- allocators/stdext::allocator_base::max_size
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocator_base [C++]
- stdext::allocators [C++], allocator_base
- stdext::allocator_base [C++], const_pointer
- stdext::allocator_base [C++], const_reference
- stdext::allocator_base [C++], difference_type
- stdext::allocator_base [C++], pointer
- stdext::allocator_base [C++], reference
- stdext::allocator_base [C++], size_type
- stdext::allocator_base [C++], value_type
- stdext::allocator_base [C++], _Charalloc
- stdext::allocator_base [C++], _Chardealloc
- stdext::allocator_base [C++], address
- stdext::allocator_base [C++], allocate
- stdext::allocator_base [C++], construct
- stdext::allocator_base [C++], deallocate
- stdext::allocator_base [C++], destroy
- stdext::allocator_base [C++], max_size
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d99f12abb1ff9d0d26f40d41888e6db27ca48996
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="allocatorbase-class"></a>allocator_base — Klasa
Definiuje klasę podstawową i typowe funkcje niezbędne do utworzenia programu przydzielania zdefiniowane przez użytkownika z filtru synchronizacji.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Type, class Sync>  
class allocator_base
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Type`|Typ elementów przydzielonej przez program przydzielania.|  
|`Sync`|Zasady synchronizacji dla programu przydzielania, jest [sync_none — klasa](../standard-library/sync-none-class.md), [sync_per_container — klasa](../standard-library/sync-per-container-class.md), [sync_per_thread — klasa](../standard-library/sync-per-thread-class.md), lub [sync_shared — Klasa](../standard-library/sync-shared-class.md).|  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[allocator_base](#allocator_base)|Tworzy obiekt typu `allocator_base`.|  
  
### <a name="typedefs"></a>Definicje typów  
  
|||  
|-|-|  
|[const_pointer](#const_pointer)|Typ, który udostępnia stałej wskaźnika do typu obiektu zarządzanego przez program przydzielania.|  
|[const_reference](#const_reference)|Typ, który zapewnia stałą odwołanie do typu obiektu zarządzanego przez program przydzielania.|  
|[difference_type](#difference_type)|Podpisany typ całkowity może reprezentować różnica między wartościami wskaźniki do typu obiektu zarządzanego przez program przydzielania.|  
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez program przydzielania.|  
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do typu obiektu zarządzanego przez program przydzielania.|  
|[size_type](#size_type)|Sekwencja typem całkowitym bez znaku, mogącej reprezentować długość każdego obiektu klasy szablonu `allocator_base` można przydzielić.|  
|[value_type](#value_type)|Typ, który jest zarządzany przez program przydzielania.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[_Charalloc](#charalloc)|Przydziela magazynu dla tablicy typu `char`.|  
|[_Chardealloc](#chardealloc)|Zwalnia magazynu dla macierzy zawierających elementy typu `char`.|  
|[Adres](#address)|Umożliwia znalezienie adresu obiektu, którego wartość jest określona.|  
|[allocate](#allocate)|Przydziela bloku pamięci wystarczająco duże, aby przechowywać przynajmniej określoną liczbę elementów.|  
|[construct](#construct)|Tworzy określonego typu obiektu na określony adres, który został zainicjowany z określoną wartością.|  
|[Cofnięcie przydziału](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.|  
|[destroy](#destroy)|Wywołanie destruktora obiektów bez cofanie przydziału pamięci przechowywania obiektu.|  
|[max_size](#max_size)|Zwraca liczbę elementów typu `Type` który może zostać przydzielony przez obiekt klasy alokatora przed wolnej pamięci jest używany w.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="charalloc"></a>  allocator_base::_Charalloc  
 Przydziela magazynu dla tablicy typu `char`.  
  
```
char *_Charalloc(size_type count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`count`|Liczba elementów w tablicy do przydzielenia.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do przydzielonego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest używany przez kontenery, gdy skompilowano z kompilatorem, którego nie można skompilować ponownie Utwórz wiązanie. Implementuje `_Charalloc` do przydzielania zdefiniowane przez użytkownika, zwracając wynik wywołania `allocate` funkcja filtr synchronizacji.  
  
##  <a name="chardealloc"></a>  allocator_base::_Chardealloc  
 Zwalnia magazynu dla macierzy zawierających elementy typu `char`.  
  
```
void _Chardealloc(void* ptr, size_type count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ptr`|Wskaźnik do pierwszego obiektu do cofnięcia alokacji z magazynu.|  
|`count`|Liczba obiektów do cofnięcia alokacji z magazynu.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest używany przez kontenery, gdy skompilowano z kompilatorem, którego nie można skompilować ponownie Utwórz wiązanie. Implementuje `_Chardealloc` do przydzielania zdefiniowane przez użytkownika, wywołując `deallocate` funkcja filtr synchronizacji. Ptr wskaźnika musi wcześniej zwróconych przez wywołanie do `_Charalloc` dla obiekt przydzielania, który porównuje równa `*this`, przydzielania tablicy obiektów o takiej samej wielkości i typu. `_Chardealloc` nigdy nie zgłasza wyjątek.  
  
##  <a name="address"></a>  allocator_base::Address  
 Umożliwia znalezienie adresu obiektu, którego wartość jest określona.  
  
```
pointer address(reference val);

const_pointer address(const_reference val);
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Wartość kwalifikatora const ani nonconst obiektu, którego adres są wyszukiwane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości, odpowiednio, stały lub nonconst znaleźć typu const ani nonconst wskaźnik do obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest zaimplementowany dla przydzielania zdefiniowane przez użytkownika przez zwrócenie `&val`.  
  
##  <a name="allocate"></a>  allocator_base::allocate  
 Przydziela bloku pamięci wystarczająco duże, aby przechowywać przynajmniej określoną liczbę elementów.  
  
```
template <class Other>  
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`_Nx`|Liczba elementów w tablicy do przydzielenia.|  
|`_Hint`|Ten parametr jest ignorowany.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do przydzielonego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska implementuje alokacji pamięci do przydzielania zdefiniowane przez użytkownika, zwracając wynik wywołania `allocate` funkcja filtr synchronizacji typu Type `*` Jeśli `_Nx == 1`, w przeciwnym razie, zwracając wynik wywołanie `operator new(_Nx * sizeof(Type))` Rzutowanie na typ typu `*`.  
  
##  <a name="allocator_base"></a>  allocator_base::allocator_base  
 Tworzy obiekt typu `allocator_base`.  
  
```
allocator_base();

template <class Other>  
allocator_base(const allocator_base<Other, Sync>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`right`|Obiekt alokatora do skopiowania.|  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy konstrukcje konstruktora [allocator_base —](../standard-library/allocator-base-class.md) wystąpienia. Drugi konstrukcje konstruktora `allocator_base` takie wystąpienie dla żadnego `allocator_base<Type, _Sync>` wystąpienia `a`, `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`.  
  
##  <a name="const_pointer"></a>  allocator_base::const_pointer  
 Typ, który udostępnia stałej wskaźnika do typu obiektu zarządzanego przez program przydzielania.  
  
```
typedef const Type *const_pointer;
```  
  
##  <a name="const_reference"></a>  allocator_base::const_reference  
 Typ, który zapewnia stałą odwołanie do typu obiektu zarządzanego przez program przydzielania.  
  
```
typedef const Type& const_reference;
```  
  
##  <a name="construct"></a>  allocator_base::Construct  
 Tworzy określonego typu obiektu na określony adres, który został zainicjowany z określoną wartością.  
  
```
void construct(pointer ptr, const Type& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ptr`|Wskaźnik do lokalizacji, w którym ma być skonstruowany obiekt.|  
|`val`|Wartość, z którym tworzona jest zainicjowane.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest zaimplementowany dla przydzielania zdefiniowane przez użytkownika przez wywołanie metody `new((void*)ptr Type(val)`.  
  
##  <a name="deallocate"></a>  allocator_base::deallocate  
 Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.  
  
```
void deallocate(pointer ptr, size_type _Nx);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ptr`|Wskaźnik do pierwszego obiektu do cofnięcia alokacji z magazynu.|  
|`_Nx`|Liczba obiektów do cofnięcia alokacji z magazynu.|  
  
### <a name="remarks"></a>Uwagi  
 Funkcji członkowskiej jest zaimplementowany dla alokatora zdefiniowane przez użytkownika, wywołując `deallocate(ptr)` w filtrze synchronizacji `Sync` Jeśli `_Nx == 1`, w przeciwnym razie przez wywołanie metody `operator delete(_Nx * ptr)`.  
  
##  <a name="destroy"></a>  allocator_base::Destroy  
 Wywołanie destruktora obiektów bez cofanie przydziału pamięci przechowywania obiektu.  
  
```
void destroy(pointer ptr);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ptr`|Wskaźnik wyznaczenie adres obiektu, które mają zostać zniszczone.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest zaimplementowany dla przydzielania zdefiniowane przez użytkownika przez wywołanie metody `ptr->~Type()`.  
  
##  <a name="difference_type"></a>  allocator_base::difference_type  
 Podpisany typ całkowity może reprezentować różnica między wartościami wskaźniki do typu obiektu zarządzanego przez program przydzielania.  
  
```
typedef std::ptrdiff_t difference_type;
```  
  
##  <a name="max_size"></a>  allocator_base::max_size  
 Zwraca liczbę elementów typu `Type` który może zostać przydzielony przez obiekt klasy alokatora przed wolnej pamięci jest używany w.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów, które może zostać przydzielony.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest zaimplementowany dla przydzielania zdefiniowane przez użytkownika przez zwrócenie `(size_t)-1 / sizeof(Type)` Jeśli `0 < (size_t)-1 / sizeof(Type)`, w przeciwnym razie `1`.  
  
##  <a name="pointer"></a>  allocator_base::Pointer  
 Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez program przydzielania.  
  
```
typedef Type *pointer;
```  
  
##  <a name="reference"></a>  allocator_base::Reference  
 Typ, który zawiera odwołanie do typu obiektu zarządzanego przez program przydzielania.  
  
```
typedef Type& reference;
```  
  
##  <a name="size_type"></a>  allocator_base::size_type  
 Sekwencja typem całkowitym bez znaku, mogącej reprezentować długość każdego obiektu klasy szablonu `allocator_base` można przydzielić.  
  
```
typedef std::size_t size_type;
```  
  
##  <a name="value_type"></a>  allocator_base::value_type  
 Typ, który jest zarządzany przez program przydzielania.  
  
```
typedef Type value_type;
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators>](../standard-library/allocators-header.md)



