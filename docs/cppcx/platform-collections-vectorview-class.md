---
title: Platform::Collections::VectorView, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
helpviewer_keywords:
- VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
ms.openlocfilehash: 7f12c7b926cd8d3d8fc892cff6f2245e7c216219
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032229"
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView, klasa

Reprezentuje widok tylko do odczytu sekwencyjnej kolekcji obiektów, które mogą być indywidualnie dostępne przez indeks. Typ każdego obiektu w kolekcji jest określony przez parametr szablonu.

## <a name="syntax"></a>Składnia

```
template <typename T, typename E>
   ref class VectorView sealed;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ elementów zawartych `VectorView` w obiekcie.

*E*<br/>
Określa predykat binarny do testowania `T`równości z wartościami typu . Wartością domyślną jest `std::equal_to<T>`.

### <a name="remarks"></a>Uwagi

Klasa `VectorView` implementuje [interfejs windows::Foundation::Collections::IVectorView\<T>](/uwp/api/windows.foundation.collections.ivectorview-1) interfejs i obsługę iteratorów biblioteki szablonów standardowych.

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Widok vectorview::VectorView](#ctor)|Inicjuje nowe wystąpienie klasy VectorView.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Widok wektorowy::Najpierw](#first)|Zwraca iterator, który określa pierwszy element w VectorView.|
|[Widok VectorView::GetAt](#getat)|Pobiera element bieżącego VectorView, który jest wskazywany przez określony indeks.|
|[Widok VectorView::GetMany](#getmany)|Pobiera sekwencję elementów z bieżącego VectorView, począwszy od określonego indeksu.|
|[Widok vector::IndexOf](#indexof)|Wyszukuje określony element w bieżącym VectorView, a jeśli zostanie znaleziony, zwraca indeks elementu.|
|[Widok VectorView::Rozmiar](#size)|Zwraca liczbę elementów w bieżącym obiekcie VectorView.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VectorView`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Obszar nazw:** Platforma::Kolekcje

## <a name="vectorviewfirst-method"></a><a name="first"></a>VectorView::Pierwsza metoda

Zwraca iterator, który określa pierwszy element w VectorView.

### <a name="syntax"></a>Składnia

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element w VectorView.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwróconego przez First() jest przypisanie wartości zwracanej do zmiennej zadeklarowanej za pomocą słowa kluczowego **automatycznego** potrącenia typu. Na przykład `auto x = myVectorView->First();`.

## <a name="vectorviewgetat-method"></a><a name="getat"></a>VectorView::Metoda GetAt

Pobiera element bieżącego VectorView, który jest wskazywany przez określony indeks.

### <a name="syntax"></a>Składnia

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Zero-based, niepodpisane liczby całkowitej, która określa określony element w VectorView obiektu.

### <a name="return-value"></a>Wartość zwracana

Element określony przez `index` parametr. Typ elementu jest określony przez parametr szablonu VectorView, *T*.

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a>VectorView::Metoda GetMany

Pobiera sekwencję elementów z bieżącego VectorView, począwszy od określonego indeksu.

### <a name="syntax"></a>Składnia

```

virtual unsigned int GetMany(
   unsigned int startIndex,
   ::Platform::WriteOnlyArray<T>^ dest
);
```

### <a name="parameters"></a>Parametry

*Startindex*<br/>
Indeks od zera początku elementów do pobrania.

*Dest*<br/>
Po zakończeniu tej operacji tablica elementów, które `startIndex` rozpoczynają się od elementu określonego przez i koniec w ostatnim elemencie w VectorView.

### <a name="return-value"></a>Wartość zwracana

Liczba pobranych elementów.

## <a name="vectorviewindexof-method"></a><a name="indexof"></a>VectorView::IndexOf Metoda

Wyszukuje określony element w bieżącym VectorView, a jeśli zostanie znaleziony, zwraca indeks elementu.

### <a name="syntax"></a>Składnia

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Element do znalezienia.

*Indeks*<br/>
Indeks od zera towaru, `value` jeśli zostanie znaleziony parametr; w przeciwnym razie 0.

Parametr *indeksu* wynosi 0, jeśli element jest `VectorView` pierwszym elementem lub element nie został znaleziony. Jeśli wartość zwracana jest **true**, element został znaleziony i jest pierwszym elementem; w przeciwnym razie nie znaleziono elementu.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli zostanie znaleziony określony element; w przeciwnym razie **false**.

## <a name="vectorviewsize-method"></a><a name="size"></a>VectorView::Metoda rozmiaru

Zwraca liczbę elementów w bieżącym obiekcie VectorView.

### <a name="syntax"></a>Składnia

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w bieżącym VectorView.

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a>VectorView::Konstruktor VectorView

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

*Init*<br/>
Typ kolekcji obiektów, który jest używany do inicjowania bieżącego VectorView.

*Il*<br/>
A [std::initializer_list](../standard-library/initializer-list-class.md) którego elementy będą używane do inicjowania VectorView.

*N*<br/>
Liczba elementów w kolekcji obiektów, który jest używany do inicjowania bieżącego VectorView.

*Rozmiar*<br/>
Liczba elementów w VectorView.

*value*<br/>
Wartość, która jest używana do inicjowania każdego elementu w bieżącym VectorView.

*v*<br/>
[Wartość Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::vector,](../standard-library/vector-class.md) który jest używany do inicjowania bieżącego VectorView.

*Ptr*<br/>
Wskaźnik do, `std::vector` który jest używany do inicjowania bieżącego VectorView.

*Arr*<br/>
A [Platform::Array](../cppcx/platform-array-class.md) obiektu, który jest używany do inicjowania bieżącego VectorView.

*A*<br/>
Obiekt [std::array,](../standard-library/array-class-stl.md) który jest używany do inicjowania bieżącego widoku VectorView.

*Pierwszym*<br/>
Pierwszy element w sekwencji obiektów, które są używane do inicjowania bieżącego VectorView. Rodzaj `first` jest przekazywana za pomocą *doskonałego spedycji.* Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*Ostatnio*<br/>
Ostatni element w sekwencji obiektów, które są używane do inicjowania bieżącego VectorView. Rodzaj `last` jest przekazywana za pomocą *doskonałego spedycji.* Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](platform-namespace-c-cx.md)<br/>
[Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
