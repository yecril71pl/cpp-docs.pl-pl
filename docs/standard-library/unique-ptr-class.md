---
title: "unique_ptr — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::unique_ptr
- memory/std::unique_ptr::deleter_type
- memory/std::unique_ptr::element_type
- memory/std::unique_ptr::pointer
- memory/std::unique_ptr::get
- memory/std::unique_ptr::get_deleter
- memory/std::unique_ptr::release
- memory/std::unique_ptr::reset
- memory/std::unique_ptr::swap
dev_langs: C++
helpviewer_keywords:
- std::unique_ptr [C++]
- std::unique_ptr [C++], deleter_type
- std::unique_ptr [C++], element_type
- std::unique_ptr [C++], pointer
- std::unique_ptr [C++], get
- std::unique_ptr [C++], get_deleter
- std::unique_ptr [C++], release
- std::unique_ptr [C++], reset
- std::unique_ptr [C++], swap
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba6ac8e50764801052c051703a211c4605a33601
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="uniqueptr-class"></a>unique_ptr — Klasa
Przechowuje wskaźnik do obiektu należące do firmy lub tablicy. Obiekt/tablicy jest własnością nie innych `unique_ptr`. Obiekt/tablicy zostanie zniszczony podczas `unique_ptr` zostanie zniszczony.  
  
## <a name="syntax"></a>Składnia  
```  
class unique_ptr {
public:
    unique_ptr();
    unique_ptr(nullptr_t Nptr);
    explicit unique_ptr(pointer Ptr);
    unique_ptr(pointer Ptr,
        typename conditional<is_reference<Del>::value, Del,
        typename add_reference<const Del>::type>::type Deleter);
    unique_ptr(pointer Ptr,
        typename remove_reference<Del>::type&& Deleter);
    unique_ptr(unique_ptr&& Right);
    template <class T2, Class Del2>
    unique_ptr(unique_ptr<T2, Del2>&& Right);
    unique_ptr(const unique_ptr& Right) = delete;
    unique_ptr& operator=(const unique_ptr& Right) = delete;
};

//Specialization for arrays:  
template <class T, class D>
class unique_ptr<T[], D> {
public:
    typedef pointer;
    typedef T element_type;
    typedef D deleter_type;
    constexpr unique_ptr() noexcept;
    template <class U>
    explicit unique_ptr(U p) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    unique_ptr(unique_ptr&& u) noexcept;
    constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }     template <class U, class E>
        unique_ptr(unique_ptr<U, E>&& u) noexcept;
    ~unique_ptr();
    unique_ptr& operator=(unique_ptr&& u) noexcept;
    template <class U, class E>
    unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;
    unique_ptr& operator=(nullptr_t) noexcept;
    T& operator[](size_t i) const;


    pointer get() const noexcept;
    deleter_type& get_deleter() noexcept;
    const deleter_type& get_deleter() const noexcept;
    explicit operator bool() const noexcept;
    pointer release() noexcept;
    void reset(pointer p = pointer()) noexcept;
    void reset(nullptr_t = nullptr) noexcept;
    template <class U>
    void reset(U p) noexcept = delete;
    void swap(unique_ptr& u) noexcept;  // disable copy from lvalue unique_ptr(const unique_ptr&) = delete;  
    unique_ptr& operator=(const unique_ptr&) = delete;
};
```  
  
#### <a name="parameters"></a>Parametry  
 `Right`  
 A `unique_ptr`.  
  
 `Nptr`  
 `rvalue` Typu `std::nullptr_t`.  
  
 `Ptr`  
 A `pointer`.  
  
 `Deleter`  
 A `deleter` funkcja, która jest powiązana z `unique_ptr`.  
  
## <a name="exceptions"></a>Wyjątki  
 Żadne wyjątki są generowane przez `unique_ptr`.  
  
## <a name="remarks"></a>Uwagi  
 `unique_ptr` Zastępuje klasy `auto_ptr`i może być używany jako element kontenerów standardowa biblioteka C++.  
  
 Użyj [make_unique](../standard-library/memory-functions.md#make_unique) funkcja pomocnika służąca do wydajnie tworzyć nowe wystąpienia klasy `unique_ptr`.  
  
 `unique_ptr`zarządza jednoznacznie zasobu. Każdy `unique_ptr` obiekt przechowuje wskaźnik do obiektu jest właścicielem lub przechowuje wskaźnika o wartości null. Zasób może należeć do nie więcej niż jednego `unique_ptr` obiekt;  gdy `unique_ptr` obiektu, który jest właścicielem określonego zasobu, zasób zostanie zwolniona. A `unique_ptr` obiektu może być przeniesiony, ale nie został skopiowany;  Aby uzyskać więcej informacji, zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 Zasób zostanie zwolniona przez wywołanie metody przechowywanych `deleter` typu obiektu `Del` który zna sposób przydzielania zasobów dla określonego `unique_ptr`. Wartość domyślna `deleter` `default_delete<T>` przyjęto założenie, że zasobu wskazywanego przez `ptr` przydzielonych za pomocą `new`, i który może być zwolniony przez wywołanie metody `delete _Ptr`. (Częściowa specjalizacja `unique_ptr<T[]>`zarządza tablicy obiektów przydzielonych za pomocą `new[]`, i ma domyślnie `deleter` `default_delete<T[]>`, wyspecjalizowany wywołać delete [] `ptr`.)  
  
 Przechowywane wskaźnik do należących do zasobów `stored_ptr` ma typ `pointer`. Jest `Del::pointer` Jeśli została zdefiniowana, a `T *` , jeśli nie. Zapisana `deleter` obiektu `stored_deleter` zajmuje bez spacji w obiekcie, jeśli `deleter` jest bezstanowe. Należy pamiętać, że `Del` może być typem referencyjnym.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[unique_ptr](#unique_ptr)|Istnieje siedem konstruktory `unique_ptr`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[deleter_type](#deleter_type)|Synonim parametru szablonu `Del`.|  
|[ELEMENT_TYPE](#element_type)|Synonim parametru szablonu `T`.|  
|[wskaźnik](#pointer)|Jest to synonim `Del::pointer` Jeśli zdefiniowane, w przeciwnym razie `T *`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[get](#get)|Zwraca `stored_ptr`.|  
|[get_deleter —](#get_deleter)|Zwraca odwołanie do `stored_deleter`.|  
|[zlecenia](#release)|przechowuje `pointer()` w `stored_ptr` i zwraca jego poprzedniej zawartości.|  
|[Resetowanie](#reset)|Zwalnia aktualnie posiadany zasób i akceptuje nowy zasób.|  
|[swap](#swap)|Zamienia zasobów i `deleter` się za pomocą podanych `unique_ptr`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|`operator bool`|Zwraca wartość typu, który można przekonwertować na typ `bool`. Wynik konwersji na `bool` jest `true` podczas `get() != pointer()`, w przeciwnym razie `false`.|  
|`operator->`|Zwraca funkcję elementu członkowskiego `stored_ptr`.|  
|`operator*`|Zwraca funkcję elementu członkowskiego `*stored_ptr`.|  
|[unique_ptr operator =](#unique_ptr_operator_eq)|Przypisuje wartość `unique_ptr` (lub `pointer-type`) do bieżącego `unique_ptr`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<pamięci >  
  
 **Namespace:** Standard  
  
##  <a name="deleter_type"></a>deleter_type  
 Typ jest synonimem parametru szablonu `Del`.  
  
```  
typedef Del deleter_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Del`.  
  
##  <a name="element_type"></a>ELEMENT_TYPE  
 Typ jest synonimem parametru szablonu `Type`.  
  
```  
typedef Type element_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Ty`.  
  
##  <a name="get"></a>unique_ptr::Get  
 Zwraca `stored_ptr`.  
  
```  
pointer get() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca funkcję elementu członkowskiego `stored_ptr`.  
  
##  <a name="get_deleter"></a>unique_ptr::get_deleter  
 Zwraca odwołanie do `stored_deleter`.  
  
```  
Del& get_deleter();

const Del& get_deleter() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca odwołanie do `stored_deleter`.  
  
##  <a name="unique_ptr_operator_eq"></a>unique_ptr operator =  
 Przypisuje adres dostarczonych `unique_ptr` do bieżącej.  
  
```  
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>  
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```  
  
### <a name="parameters"></a>Parametry  
 A `unique_ptr` odwołania przypisywać wartości do bieżącego `unique_ptr`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie wywołania `reset(right.release())` i Przenieś `right.stored_deleter` do `stored_deleter`, następnie zwracany `*this`.  
  
##  <a name="pointer"></a>wskaźnik  
 Jest to synonim `Del::pointer` Jeśli zdefiniowane, w przeciwnym razie `Type *`.  
  
```  
typedef T1 pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem `Del::pointer` Jeśli zdefiniowane, w przeciwnym razie `Type *`.  
  
##  <a name="release"></a>unique_ptr::Release  
 Zwalnia własność zwrócony przechowywanych wskaźnik do obiektu wywołującego i ustawia wartość wskaźnika przechowywanych `nullptr`.  
  
```  
pointer release();
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj `release` do Przejmij na własność raw wskaźnika przechowywane przez `unique_ptr`. Element wywołujący jest odpowiedzialny za usunięcie wskaźnika zwrócony. `unique-ptr` Ustawiono skonstruowany domyślnego stanu pustego. Można przypisać innego wskaźnika zgodne z typem `unique_ptr` po wywołaniu `release`.  
  
### <a name="example"></a>Przykład  
  Ten przykład przedstawia, jak jest odpowiedzialny za zwrócony obiekt wywołujący wersji:  
  
```cpp  
// stl_release_unique.cpp  
// Compile by using: cl /W4 /EHsc stl_release_unique.cpp  
#include <iostream>  
#include <memory>  
  
struct Sample {  
   int content_;  
   Sample(int content) : content_(content) {  
      std::cout << "Constructing Sample(" << content_ << ")" << std::endl;  
   }  
   ~Sample() {  
      std::cout << "Deleting Sample(" << content_ << ")" << std::endl;  
   }  
};  
  
void ReleaseUniquePointer() {  
   // Use make_unique function when possible.    
   auto up1 = std::make_unique<Sample>(3);  
   auto up2 = std::make_unique<Sample>(42);  
  
   // Take over ownership from the unique_ptr up2 by using release  
   auto ptr = up2.release();  
   if (up2) {  
      // This statement does not execute, because up2 is empty.  
      std::cout << "up2 is not empty." << std::endl;  
   }  
   // We are now responsible for deletion of ptr.  
   delete ptr;  
   // up1 deletes its stored pointer when it goes out of scope.     
}  
  
int main() {  
   ReleaseUniquePointer();  
}  
```  
  
  Wyjście z komputera:  
  
```Output  
Constructing Sample(3)  
Constructing Sample(42)  
Deleting Sample(42)  
Deleting Sample(3)  
  
```  
  
##  <a name="reset"></a>unique_ptr::reset  
 Przejmuje parametr wskaźnika, a następnie usunięcie oryginalnego przechowywanych wskaźnika. Jeśli nowy wskaźnik jest taka sama jak oryginalny wskaźnik przechowywane, `reset` usuwa wskaźnik i ustawia wskaźnik przechowywanych `nullptr`.  
  
```  
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ptr`|Wskaźnik do zasobu, aby przejąć na własność.|  
  
### <a name="remarks"></a>Uwagi  
 Użyj `reset` zmienić zapisana [wskaźnika](#pointer) własnością `unique_ptr` do `ptr` , a następnie usuń oryginalny wskaźnik przechowywane. Jeśli `unique_ptr` nie jest pusty, `reset` wywołuje zwrócona przez funkcję deleter [get_deleter](#get_deleter) oryginalnego wskaźnika przechowywane.  
  
 Ponieważ `reset` najpierw przechowuje nowego wskaźnika `ptr`, a następnie usunięcie oryginalnego wskaźnika przechowywane, istnieje możliwość `reset` można natychmiast usunąć `ptr` Jeśli jest taka sama jak oryginalny wskaźnik przechowywane.  
  
##  <a name="swap"></a>unique_ptr::swap  
 Zamienia wskaźniki między dwiema `unique_ptr` obiektów.  
  
```  
void swap(unique_ptr& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 A `unique_ptr` używany do wymiany wskaźników.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zamienia `stored_ptr` z `right.stored_ptr` i `stored_deleter` z `right.stored_deleter`.  
  
##  <a name="unique_ptr"></a>unique_ptr::unique_ptr  
 Istnieje siedem konstruktory `unique_ptr`.  
  
```  
unique_ptr();

unique_ptr(nullptr_t);
explicit unique_ptr(pointer ptr);

unique_ptr(
    Type* ptr,  
    typename conditional<
    is_reference<Del>::value, 
    Del, 
    typename add_reference<const Del>::type>::type _Deleter);

unique_ptr(pointer ptr, typename remove_reference<Del>::type&& _Deleter);
unique_ptr(unique_ptr&& right);
template <class Ty2, Class Del2>  
unique_ptr(unique_ptr<Ty2, Del2>&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ptr`|Wskaźnik do zasobów, które ma być przypisany do`unique_ptr.`|  
|`_Deleter`|A `deleter` do przypisania do `unique_ptr`.|  
|`right`|`rvalue reference` Do `unique_ptr` z którego `unique_ptr` pola są przenoszenia przypisane do nowo utworzone `unique_ptr`.|  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze dwa konstruktory utworzenia obiektu zarządzanego przez żaden z zasobów. Trzeci magazynów konstruktora `ptr` w `stored_ptr`. Czwarty magazynów konstruktora `ptr` w `stored_ptr` i `deleter` w `stored_deleter`.  
  
 Piąty magazynów konstruktora `ptr` w `stored_ptr` i przenosi `deleter` do `stored_deleter`. Magazyn konstruktorów szóstego lub siódmego `right.release()` w `stored_ptr` i przenosi `right.get_deleter()` do `stored_deleter`.  
  
##  <a name="dtorunique_ptr"></a>unique_ptr ~ unique_ptr  
 Destruktor dla elementu `unique_ptr`, niszczy `unique_ptr` obiektu.  
  
```  
~unique_ptr();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania destruktora `get_deleter()(stored_ptr)`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<pamięci >](../standard-library/memory.md)


