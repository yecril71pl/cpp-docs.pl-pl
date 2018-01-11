---
title: Klasa platform::Collections::Vector | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLECTION/Platform::Collections::Vector::Vector
- COLLECTION/Platform::Collections::Vector::Append
- COLLECTION/Platform::Collections::Vector::Clear
- COLLECTION/Platform::Collections::Vector::First
- COLLECTION/Platform::Collections::Vector::GetAt
- COLLECTION/Platform::Collections::Vector::GetMany
- COLLECTION/Platform::Collections::Vector::GetView
- COLLECTION/Platform::Collections::Vector::IndexOf
- COLLECTION/Platform::Collections::Vector::InsertAt
- COLLECTION/Platform::Collections::Vector::ReplaceAll
- COLLECTION/Platform::Collections::Vector::RemoveAt
- COLLECTION/Platform::Collections::Vector::RemoveAtEnd
- COLLECTION/Platform::Collections::Vector::SetAt
- COLLECTION/Platform::Collections::Vector::Size
- COLLECTION/Platform::Collections::Vector::VectorChanged
dev_langs: C++
helpviewer_keywords: Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8c371b6805616ff0b114be24bb291469eae2dd26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="platformcollectionsvector-class"></a>Klasa platform::Collections::Vector
Reprezentuje sekwencyjną kolekcją obiektów, których można indywidualnie uzyskać dostęp przez indeks.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename T, typename E>  
   ref class Vector sealed;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ elementów zawartych w tym obiekcie wektora.  
  
 `E`  
 Określa binarne predykatu testowania równości z wartościami typu `T`. Wartość domyślna to `std::equal_to<T>`.  
  
### <a name="remarks"></a>Uwagi  
 Dozwolone typy to:  
  
1.  liczby całkowite  
  
2.  Klasa interfejsu ^  
  
3.  Klasa ref publicznego ^  
  
4.  wartość — Struktura  
  
5.  Wyliczenie publiczne — klasa  
  
 Klasa Vector jest C++ wykonanie [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) interfejsu.  
  
 W przypadku próby użycia typu wektora publiczny zwraca wartość lub parametr C3986 zostanie wygenerowany błąd kompilatora. Można naprawić błąd, zmieniając parametr lub zwracany typ wartości do [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410). Aby uzyskać więcej informacji, zobacz [kolekcji (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Vector::Vector](#ctor)|Inicjuje nowe wystąpienie klasy wektora.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Vector::append](#append)|Wstawia określony element za ostatnim elementem w bieżącym wektora.|  
|[Vector::Clear](#clear)|Usuwa wszystkie elementy w bieżącym wektora.|  
|[Vector::First](#first)|Zwraca wartość określającą pierwszego elementu w wektorze iteratora.|  
|[Vector::GetAt](#getat)|Pobiera element bieżącej wektora, którego jest identyfikować przy określonym indeksie.|  
|[Vector::GetMany](#getmany)|Pobiera sekwencję elementów z bieżącym wektora, zaczynając od określonego indeksu.|  
|[Vector::GetView](#getview)|Zwraca wektor; widok tylko do odczytu oznacza to [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md).|  
|[Vector::IndexOf](#indexof)|Wyszukuje określony element w zakresie bieżącego ataku i jeśli znaleziona, zwraca indeks elementu.|  
|[Vector::InsertAt](#insertat)|Wstawia określony element do bieżącego wektora po elemencie identyfikowana na podstawie określonego indeksu.|  
|[Vector::ReplaceAll](#replaceall)|Usuwa elementy w zakresie bieżącego ataku i wstawia elementy z określonej tablicy.|  
|[Vector::RemoveAt](#removeat)|Usuwa element identyfikowane przez określony indeks z bieżącym wektora.|  
|[Vector::RemoveAtEnd](#removeatend)|Usuwa element na koniec bieżącego wektora.|  
|[Vector::SetAt](#setat)|Przypisuje wartość określonego elementu w bieżącym wektora, identyfikowany przez określony indeks.|  
|[Vector::size](#size)|Zwraca liczbę elementów w bieżącym obiekcie wektora.|  
  
### <a name="events"></a>Zdarzenia  
  
|||  
|-|-|  
|Nazwa|Opis|  
|zdarzenia [Windows::Foundation::Collection::VectorChangedEventHandler\<T > ^ VectorChanged](http://go.microsoft.com/fwlink/p/?LinkId=262644)|Występuje, gdy wektora.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Vector`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="append"></a>Vector::append — metoda
Wstawia określony element za ostatnim elementem w bieżącym wektora.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual void Append(T item);  
```  
  
### <a name="parameters"></a>Parametry  
 `index`  
 Element do wstawienia do wektora. Typ `item` jest definiowana za pomocą *T* typename.  
  


## <a name="clear"></a>Vector::Clear — metoda
Usuwa wszystkie elementy w bieżącym wektora.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual void Clear();  
```   


## <a name="first"></a>Vector::First — metoda
Zwraca iteratora tego do pierwszego elementu w wektorze.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
virtual Windows::Foundation::Collections::IIterator <T>^ First();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora wskazujące pierwszy element w wektorze.  
  
### <a name="remarks"></a>Uwagi  
 Jest to wygodny sposób przechowywania iteratora zwrócony przez First() można przypisać do zmiennej, która jest zadeklarowana z wartością zwracaną **automatycznie** wpisz wnioskowanie — słowo kluczowe. Na przykład `auto x = myVector->First();`. Ta iteratora wie długości kolekcji.  
  
 Para Iteratory do przekazania do funkcji STL, użyj funkcji wolnego [Windows::Foundation::Collections:: rozpocząć](../cppcx/begin-function.md) i [Windows::Foundation::Collections::end](../cppcx/end-function.md)  
  


## <a name="getat"></a>Vector::GetAt — metoda
Pobiera element bieżącej wektora, którego jest identyfikować przy określonym indeksie.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual T GetAt(unsigned int index);  
```  
  
### <a name="parameters"></a>Parametry  
 `index`  
 Liczony od zera, bez znaku liczba całkowita określająca dany element w obiekt wektora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określony przez element `index` parametru. Typ elementu jest określany przez *T* typename.  
  


## <a name="getmany"></a>Vector::GetMany — metoda
Pobiera sekwencję elementów z bieżącym wektora, zaczynając od określonego indeksu i kopiuje je do tablicy przydzielone przez obiekt wywołujący.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual unsigned int GetMany(
    unsigned int startIndex, 
    Platform::WriteOnlyArray<T>^ dest);  
```  
  
### <a name="parameters"></a>Parametry  
 `startIndex`  
 Liczony od zera indeks początku elementów do pobrania.  
  
 `dest`  
 Przydzielone przez obiekt wywołujący tablica elementów, które rozpoczynają się określony przez element `startIndex` i na końcu ostatniego elementu w wektorze.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów pobranych.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie jest przeznaczony do użycia bezpośrednio przez kod klienta. Jest używana wewnętrznie w [to_vector funkcja](../cppcx/to-vector-function.md) umożliwia wydajne konwersja Platform::Vector intances std::vector wystąpień.  
  


## <a name="getview"></a>Vector::GetView — metoda
Zwraca wektor; widok tylko do odczytu oznacza to, IVectorView.  
  
### <a name="syntax"></a>Składnia  
  
```    
Windows::Foundation::Collections::IVectorView<T>^ GetView();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt IVectorView.  
  


## <a name="indexof"></a>Vector::IndexOf — metoda
Wyszukuje określony element w zakresie bieżącego ataku i jeśli znaleziona, zwraca indeks elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
virtual bool IndexOf(T value, unsigned int* index);  
```  
  
### <a name="parameters"></a>Parametry  
 `value`  
 Aby znaleźć element.  
  
 `index`  
 Liczony od zera indeks elementu Jeśli parametr `value` zostanie odnaleziony; w przeciwnym razie wartość 0.  
  
 `index` Parametru jest 0, jeśli element jest pierwszym elementem wektora lub element nie został znaleziony. Jeśli wartość zwracana jest `true`, element został odnaleziony i jest pierwszym elementem; w przeciwnym razie nie odnaleziono elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli określony element zostanie odnaleziony; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 IndexOf używa std::find_if, aby znaleźć element. Typy elementu niestandardowego, w związku z tym powinien przeciążać == i! = — operator w celu umożliwienia równości wymaga tego find_if porównania.  
  


##  <a name="insertat"></a>Vector::InsertAt — metoda
Wstawia określony element do bieżącego wektora po elemencie identyfikowana na podstawie określonego indeksu.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual void InsertAt(unsigned int index, T item)  
```  
  
### <a name="parameters"></a>Parametry  
 `index`  
 Liczony od zera, bez znaku liczba całkowita określająca dany element w obiekt wektora.  
  
 `item`  
 Element do wstawienia do wektora po określony przez element `index`. Typ `item` jest definiowana za pomocą *T* typename.  
  


## <a name="removeat"></a>Vector::RemoveAt — metoda
Usuwa element identyfikowane przez określony indeks z bieżącym wektora.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual void RemoveAt(unsigned int index);  
```  
  
### <a name="parameters"></a>Parametry  
 `index`  
 Liczony od zera, bez znaku liczba całkowita określająca dany element w obiekt wektora.  
  


## <a name="removeatend"></a>Vector::RemoveAtEnd — metoda
Usuwa element na koniec bieżącego wektora.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual void RemoveAtEnd();  
```  
  


## <a name="replaceall"></a>Vector::ReplaceAll — metoda
Usuwa elementy w zakresie bieżącego ataku i wstawia elementy z określonej tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);  
```  
  
### <a name="parameters"></a>Parametry  
 `arr`  
 Tablica obiektów, którego typ jest zdefiniowany przez *T* typename.  
  


## <a name="setat"></a>Vector::SetAt — metoda
Przypisuje wartość określonego elementu w bieżącym wektora, identyfikowany przez określony indeks.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual void SetAt(unsigned int index, T item);  
```  
  
### <a name="parameters"></a>Parametry  
 `index`  
 Liczony od zera, bez znaku liczba całkowita określająca dany element w obiekt wektora.  
  
 `item`  
 Wartość do przypisania do określonego elementu. Typ `item` jest definiowana za pomocą *T* typename.  
  


## <a name="size"></a>Vector::size — metoda
Zwraca liczbę elementów w bieżącym obiekcie wektora.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w wektorze bieżącej.  
  


## <a name="ctor"></a>Vector::Vector — Konstruktor
Inicjuje nowe wystąpienie klasy wektora.  
  
### <a name="syntax"></a>Składnia  
  
```  
Vector();  
  
explicit Vector(unsigned int size);  
Vector( unsigned int size, T value);    
template <typename U> explicit Vector( const ::std::vector<U>& v);    
template <typename U> explicit Vector( std::vector<U>&& v);    

Vector( const T * ptr, unsigned int size);    
template <size_t N> explicit Vector(const T(&arr)[N]);    
template <size_t N> explicit Vector(const std::array<T, N>& a);   
explicit Vector(const Array<T>^ arr);  
  
template <typename InIt> Vector(InIt first, InIt last);   
Vector(std::initializer_list<T> il);  
```  
  
### <a name="parameters"></a>Parametry  
 A  
 A [std::array](../standard-library/array-class-stl.md) posłuży wektor inicjowania.  
  
 A  
 A [Platform::Array](../cppcx/platform-array-class.md) posłuży wektor inicjowania.  
  
 `InIt`  
 Typ kolekcji obiektów jest używana do bieżącego wektor inicjowania.  
  
 Il  
 A [std::initializer_list](../standard-library/initializer-list-class.md) obiektów typu `T` posłuży wektor inicjowania.  
  
 `N`  
 Liczba elementów w kolekcji obiektów, które służy do bieżącego wektor inicjowania.  
  
 `size`  
 Liczba elementów w wektorze.  
  
 `value`  
 Wartość, która jest używana do każdego elementu w bieżącym wektor inicjowania.  
  
 `v`  
 [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::vector](../standard-library/vector-class.md) używany bieżący wektor inicjowania.  
  
 `ptr`  
 Wskaźnik do `std::vector` używany bieżący wektor inicjowania.  
  
 `arr`  
 A [Platform::Array](../cppcx/platform-array-class.md) obiekt, który służy do bieżącego wektor inicjowania.  
  
 `a`  
 A [std::array](../standard-library/array-class-stl.md) obiekt, który służy do bieżącego wektor inicjowania.  
  
 `first`  
 Pierwszym elementem w sekwencji obiektów, które są używane do bieżącego wektor inicjowania. Typ `first` jest przekazywany za pomocą klasy *doskonała przekazywania*. Aby uzyskać więcej informacji, zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 `last`  
 Ostatnim elementem w sekwencji obiektów, które są używane do bieżącego wektor inicjowania. Typ `last` jest przekazywany za pomocą klasy *doskonała przekazywania*. Aby uzyskać więcej informacji, zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  


  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)   
 [Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)