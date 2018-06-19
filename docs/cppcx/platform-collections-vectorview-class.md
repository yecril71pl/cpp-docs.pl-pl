---
title: Klasa platform::Collections::VectorView | Dokumentacja firmy Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 937342c340b085f2e2bdeef8ed7df21dae826152
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092913"
---
# <a name="platformcollectionsvectorview-class"></a>Klasa platform::Collections::VectorView
Reprezentuje widok tylko do odczytu sekwencyjną kolekcją obiektów, których można indywidualnie uzyskać dostęp przez indeks. Typ każdego obiektu w kolekcji jest określony przez parametr szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename T, typename E>  
   ref class VectorView sealed;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ elementów zawartych w `VectorView` obiektu.  
  
 `E`  
 Określa binarne predykatu testowania równości z wartościami typu `T`. Wartość domyślna to `std::equal_to<T>`.  
  
### <a name="remarks"></a>Uwagi  
 `VectorView` Klasa implementuje [Windows::Foundation::Collections::IVectorView\<T >](http://go.microsoft.com/fwlink/p/?LinkId=262411) interfejsu i obsługę Iteratory standardowa biblioteka szablonów.  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VectorView::VectorView](#ctor)|Inicjuje nowe wystąpienie klasy VectorView.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VectorView::First](#first)|Zwraca określający pierwszego elementu w VectorView iteratora.|  
|[VectorView::GetAt](#getat)|Pobiera element VectorView bieżącej, wskazaną przez określonego indeksu.|  
|[VectorView::GetMany](#getmany)|Pobiera sekwencję elementów z bieżącym VectorView, zaczynając od określonego indeksu.|  
|[VectorView::IndexOf](#indexof)|Wyszukuje określony element w bieżącym VectorView i w razie znaleziona, zwraca indeks elementu.|  
|[VectorView::Size](#size)|Zwraca liczbę elementów w bieżącym obiekcie VectorView.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `VectorView`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="first"></a>  VectorView::First — metoda
Zwraca określający pierwszego elementu w VectorView iteratora.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<T>^   
   First();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora określający pierwszego elementu w VectorView.  
  
### <a name="remarks"></a>Uwagi  
 Jest to wygodny sposób przechowywania iteratora zwrócony przez First() można przypisać do zmiennej, która jest zadeklarowana z wartością zwracaną **automatycznie** wpisz wnioskowanie — słowo kluczowe. Na przykład `auto x = myVectorView->First();`.  
  


## <a name="getat"></a>  VectorView::GetAt — metoda
Pobiera element VectorView bieżącej, wskazaną przez określonego indeksu.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
T GetAt(  
   UInt32 index  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `index`  
 Liczony od zera, bez znaku liczba całkowita określająca, kiedy dany element w obiekcie VectorView.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określony przez element `index` parametru. Typ elementu jest określony przez parametr szablonu VectorView *T*.  
  


## <a name="getmany"></a>  VectorView::GetMany — metoda
Pobiera sekwencję elementów z bieżącym VectorView, zaczynając od określonego indeksu.  
  
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
 Po zakończeniu tej operacji, tablicę elementów, które rozpoczynają się określony przez element `startIndex` i na końcu ostatniego elementu w VectorView.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów pobranych.  
  


## <a name="indexof"></a>  VectorView::IndexOf — metoda
Wyszukuje określony element w bieżącym VectorView i w razie znaleziona, zwraca indeks elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
virtual bool IndexOf(  
   T value,  
   unsigned int* index  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `value`  
 Aby znaleźć element.  
  
 `index`  
 Liczony od zera indeks elementu Jeśli parametr `value` zostanie odnaleziony; w przeciwnym razie wartość 0.  
  
 `index` Parametru jest 0, jeśli element jest pierwszym elementem VectorView lub element nie został znaleziony. Jeśli wartość zwracana jest `true`, element został odnaleziony i jest pierwszym elementem; w przeciwnym razie nie odnaleziono elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli określony element zostanie odnaleziony; w przeciwnym razie `false`.  
  


## <a name="size"></a>  VectorView::Size — metoda
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
 Typ kolekcji obiektów służy do inicjowania VectorView bieżącej.  
  
 il  
 A [std::initializer_list](../standard-library/initializer-list-class.md) której elementy będą używać w celu inicjowania VectorView.  
  
 `N`  
 Liczba elementów w kolekcji obiektów, które służy do inicjowania VectorView bieżącej.  
  
 `size`  
 Liczba elementów w VectorView.  
  
 `value`  
 Wartość, która służy do inicjowania każdego elementu w bieżącym VectorView.  
  
 `v`  
 [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::vector](../standard-library/vector-class.md) używany do inicjowania VectorView bieżącej.  
  
 `ptr`  
 Wskaźnik do `std::vector` używany do inicjowania VectorView bieżącej.  
  
 `arr`  
 A [Platform::Array](../cppcx/platform-array-class.md) obiekt, który służy do inicjowania VectorView bieżącej.  
  
 `a`  
 A [std::array](../standard-library/array-class-stl.md) obiekt, który służy do inicjowania VectorView bieżącej.  
  
 `first`  
 Pierwszym elementem w sekwencji obiektów, które są używane do zainicjowania VectorView bieżącej. Typ `first` jest przekazywany za pomocą klasy *doskonała przekazywania*. Aby uzyskać więcej informacji, zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 `last`  
 Ostatnim elementem w sekwencji obiektów, które są używane do zainicjowania VectorView bieżącej. Typ `last` jest przekazywany za pomocą klasy *doskonała przekazywania*. Aby uzyskać więcej informacji, zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  


  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)   
 [Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)