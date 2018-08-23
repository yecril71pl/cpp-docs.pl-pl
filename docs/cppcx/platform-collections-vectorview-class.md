---
title: 'Platform::Collections:: vectorview, klasa | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
dev_langs:
- C++
helpviewer_keywords:
- VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0020937bae5f6392c7d9e5e8daf22f3cc4e6a31
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584109"
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections:: vectorview, klasa
Reprezentuje widok tylko do odczytu sekwencyjnego kolekcji obiektów, które mogą być indywidualnie uzyskać dostęp przez indeks. Typ każdego obiektu w kolekcji jest określony przez parametr szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename T, typename E>  
   ref class VectorView sealed;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ elementów zawartych w słowniku `VectorView` obiektu.  
  
 `E`  
 Określa binarny predykat równości z wartościami typu testowania `T`. Wartość domyślna to `std::equal_to<T>`.  
  
### <a name="remarks"></a>Uwagi  
 `VectorView` Klasy implementuje [Windows::Foundation::Collections::IVectorView\<T >](http://go.microsoft.com/fwlink/p/?LinkId=262411) interfejsu i pomoc techniczna dla iteratorów standardowej biblioteki szablonów.  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VectorView::VectorView](#ctor)|Inicjuje nowe wystąpienie klasy VectorView.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VectorView::First](#first)|Zwraca iterator, który określa pierwszy element w VectorView.|  
|[VectorView::GetAt](#getat)|Pobiera element bieżącego VectorView, który jest wskazywany przez określony indeks.|  
|[VectorView::GetMany](#getmany)|Pobiera sekwencję elementów z bieżącego VectorView, rozpoczynając od określonego indeksu.|  
|[VectorView::IndexOf](#indexof)|Wyszukuje określony element w bieżącym VectorView i, jeśli znaleziono zwraca indeks elementu.|  
|[VectorView::Size](#size)|Zwraca liczbę elementów w bieżącym obiekcie VectorView.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `VectorView`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="first"></a>  Metoda VectorView::First
Zwraca iterator, który określa pierwszy element w VectorView.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<T>^   
   First();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator, który określa pierwszy element w VectorView.  
  
### <a name="remarks"></a>Uwagi  
 Wygodnym sposobem przechowywania iteratorów zwróconych przez First() jest przypisanie zwracana wartość do zmiennej, która jest zadeklarowana za pomocą **automatycznie** słowem kluczowym dedukcji typu. Na przykład `auto x = myVectorView->First();`.  
  


## <a name="getat"></a>  Metoda VectorView::GetAt
Pobiera element bieżącego VectorView, który jest wskazywany przez określony indeks.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
T GetAt(  
   UInt32 index  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `index`  
 Liczony od zera, nieoznaczona liczba całkowita określająca konkretnego elementu w obiekcie VectorView.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określony przez element `index` parametru. Typ elementu jest określony przez parametr szablonu VectorView *T*.  
  


## <a name="getmany"></a>  Metoda VectorView::GetMany
Pobiera sekwencję elementów z bieżącego VectorView, rozpoczynając od określonego indeksu.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
virtual unsigned int GetMany(  
   unsigned int startIndex,   
   ::Platform::WriteOnlyArray<T>^ dest  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `startIndex`  
 Liczony od zera indeks początku elementów do pobrania.  
  
 `dest`  
 Po zakończeniu tej operacji, tablica elementów, które zaczynają się na określony przez element `startIndex` i na końcu po ostatnim elemencie w VectorView.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pobrać liczbę elementów.  
  


## <a name="indexof"></a>  Metoda VectorView::IndexOf
Wyszukuje określony element w bieżącym VectorView i, jeśli znaleziono zwraca indeks elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
virtual bool IndexOf(  
   T value,  
   unsigned int* index  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `value`  
 Element do znalezienia.  
  
 `index`  
 Liczony od zera indeks elementu Jeśli parametr `value` jest; w przeciwnym razie 0.  
  
 `index` Parametru to 0, jeśli element jest pierwszy element VectorView lub element nie został znaleziony. Jeśli wartość zwracana jest `true`, element został odnaleziony i jest pierwszy element; w przeciwnym razie nie znaleziono elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli określony element zostanie znaleziony; w przeciwnym razie `false`.  
  


## <a name="size"></a>  Metoda VectorView::Size
Zwraca liczbę elementów w bieżącym obiekcie VectorView.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w bieżącym VectorView.  
  


## <a name="ctor"></a>  Konstruktor VectorView::VectorView
Inicjuje nowe wystąpienie klasy VectorView.  
  
### <a name="syntax"></a>Składnia  
  
```  
VectorView();  
explicit VectorView(  
   UInt32 size  
);  
VectorView(  
   UInt32 size,  
   T value  
);  
explicit VectorView(  
   const ::std::vector<T>& v  
);  
explicit VectorView(  
   ::std::vector<T>&& v  
);  
VectorView(  
   const T * ptr,  
   UInt32 size  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const T (&arr)[N]  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const ::std::array<T,  
   N>& a  
);  
  
explicit VectorView(  
   const ::Platform::Array<T>^ arr  
);  
  
template <  
   typename InIt  
>  
VectorView(  
   InItfirst,  
   InItlast  
);  
  
VectorView(  
   std::initializer_list<T> il  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `InIt`  
 Typ kolekcji obiektów służy do inicjowania VectorView bieżącego.  
  
 il  
 A [std::initializer_list](../standard-library/initializer-list-class.md) której elementy będzie można użyć do zainicjowania VectorView.  
  
 `N`  
 Liczba elementów w kolekcji obiektów, które służy do inicjowania VectorView bieżącego.  
  
 `size`  
 Liczba elementów w VectorView.  
  
 `value`  
 Wartość, która służy do inicjowania każdego elementu w bieżącym VectorView.  
  
 `v`  
 [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::vector](../standard-library/vector-class.md) używany do zainicjowania VectorView bieżącego.  
  
 `ptr`  
 Wskaźnik do `std::vector` używany do zainicjowania VectorView bieżącego.  
  
 `arr`  
 A [Platform::Array](../cppcx/platform-array-class.md) obiekt, który służy do inicjowania VectorView bieżącego.  
  
 `a`  
 A [std::array](../standard-library/array-class-stl.md) obiekt, który służy do inicjowania VectorView bieżącego.  
  
 `first`  
 Pierwszy element w sekwencji obiektów, które są stosowane do inicjalizacji VectorView bieżącego. Typ `first` jest przekazywany przez *doskonała przekazywania*. Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 `last`  
 Ostatniego elementu w sekwencji obiektów, które są stosowane do inicjalizacji VectorView bieżącego. Typ `last` jest przekazywany przez *doskonała przekazywania*. Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  


  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)   
 [Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)