---
title: 'Platform:: Collections:: VectorView, Klasa'
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
ms.openlocfilehash: 207f5d517eaae475af1c65a284a3d1ebe50621af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218393"
---
# <a name="platformcollectionsvectorview-class"></a>Platform:: Collections:: VectorView, Klasa

Przedstawia widok tylko do odczytu sekwencyjnej kolekcji obiektów, do których można uzyskać dostęp za pomocą indeksu. Typ każdego obiektu w kolekcji jest określany przez parametr szablonu.

## <a name="syntax"></a>Składnia

```
template <typename T, typename E>
   ref class VectorView sealed;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ elementów zawartych w `VectorView` obiekcie.

*Adres*<br/>
Określa Predykat binarny na potrzeby testowania równości z wartościami typu `T` . Wartość domyślna to `std::equal_to<T>`.

### <a name="remarks"></a>Uwagi

`VectorView`Klasa implementuje interfejs [systemu Windows:: Foundation:: Collections:: \<T> IVectorView](/uwp/api/windows.foundation.collections.ivectorview-1) i obsługuje Iteratory standardowej biblioteki szablonów.

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VectorView::VectorView](#ctor)|Inicjuje nowe wystąpienie klasy VectorView.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VectorView:: First](#first)|Zwraca iterator, który określa pierwszy element w VectorView.|
|[VectorView::GetAt](#getat)|Pobiera element bieżącego VectorView, który jest wskazywany przez określony indeks.|
|[VectorView:: getwiele](#getmany)|Pobiera sekwencję elementów z bieżącego VectorView, rozpoczynając od określonego indeksu.|
|[VectorView:: IndexOf](#indexof)|Wyszukuje określony element w bieżącym VectorView i jeśli zostanie znaleziony, zwraca indeks elementu.|
|[VectorView:: size](#size)|Zwraca liczbę elementów w bieżącym obiekcie VectorView.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VectorView`

### <a name="requirements"></a>Wymagania

**Nagłówek:** Collection. h

**Przestrzeń nazw:** Platform:: Collections

## <a name="vectorviewfirst-method"></a><a name="first"></a>VectorView:: First — Metoda

Zwraca iterator, który określa pierwszy element w VectorView.

### <a name="syntax"></a>Składnia

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element w VectorView.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwracanego przez First () jest przypisanie wartości zwracanej do zmiennej, która jest zadeklarowana za pomocą **`auto`** słowa kluczowego odejmowania. Na przykład `auto x = myVectorView->First();`.

## <a name="vectorviewgetat-method"></a><a name="getat"></a>VectorView:: GetAt, Metoda

Pobiera element bieżącego VectorView, który jest wskazywany przez określony indeks.

### <a name="syntax"></a>Składnia

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>Parametry

*indeks*<br/>
Liczba całkowita bez znaku równa zero, która określa konkretny element w obiekcie VectorView.

### <a name="return-value"></a>Wartość zwracana

Element określony przez `index` parametr. Typ elementu jest określony przez parametr szablonu VectorView, *T*.

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a>VectorView:: getwiele — Metoda

Pobiera sekwencję elementów z bieżącego VectorView, rozpoczynając od określonego indeksu.

### <a name="syntax"></a>Składnia

```

virtual unsigned int GetMany(
   unsigned int startIndex,
   ::Platform::WriteOnlyArray<T>^ dest
);
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Liczony od zera indeks początku elementów do pobrania.

*dest*<br/>
Po zakończeniu tej operacji Tablica elementów, która rozpoczyna się od elementu określonego przez `startIndex` i kończy się na ostatnim elemencie w VectorView.

### <a name="return-value"></a>Wartość zwracana

Liczba pobranych elementów.

## <a name="vectorviewindexof-method"></a><a name="indexof"></a>VectorView:: IndexOf, Metoda

Wyszukuje określony element w bieżącym VectorView i jeśli zostanie znaleziony, zwraca indeks elementu.

### <a name="syntax"></a>Składnia

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>Parametry

*wartościami*<br/>
Element do znalezienia.

*indeks*<br/>
Indeks (liczony od zera) elementu, jeśli parametr `value` zostanie znaleziony; w przeciwnym razie 0.

Parametr *index* ma wartość 0, jeśli element jest pierwszym elementem `VectorView` lub nie znaleziono elementu. Jeśli zwracana wartość to **`true`** , element został znaleziony i jest pierwszym elementem; w przeciwnym razie element nie został znaleziony.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli określony element zostanie znaleziony; w przeciwnym razie **`false`** .

## <a name="vectorviewsize-method"></a><a name="size"></a>VectorView:: size — Metoda

Zwraca liczbę elementów w bieżącym obiekcie VectorView.

### <a name="syntax"></a>Składnia

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w bieżącym VectorView.

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a>VectorView:: VectorView — Konstruktor

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

*InIt*<br/>
Typ kolekcji obiektów, który jest używany do inicjowania bieżącego VectorView.

*II*<br/>
[Std:: initializer_list](../standard-library/initializer-list-class.md) , którego elementy zostaną użyte do zainicjowania VectorView.

*N*<br/>
Liczba elementów w kolekcji obiektów, które są używane do inicjowania bieżącego VectorView.

*zmienia*<br/>
Liczba elementów w VectorView.

*wartościami*<br/>
Wartość, która jest używana do inicjowania każdego elementu w bieżącym VectorView.

*v*<br/>
[Lvalues i rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std:: Vector](../standard-library/vector-class.md) , który jest używany do inicjowania bieżącego VectorView.

*ptr*<br/>
Wskaźnik do elementu `std::vector` , który jest używany do inicjowania bieżącego VectorView.

*Genotyp*<br/>
Obiekt [platform:: Array](../cppcx/platform-array-class.md) , który jest używany do inicjowania bieżącego VectorView.

*z*<br/>
Obiekt [std:: Array](../standard-library/array-class-stl.md) , który jest używany do inicjowania bieżącego VectorView.

*pierwszego*<br/>
Pierwszy element w sekwencji obiektów, który jest używany do inicjowania bieżącego VectorView. Typ `first` jest przekazywana za pomocą *doskonałego przekazywania*. Aby uzyskać więcej informacji, zobacz [rvalue Reference deklarator:  &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*ostatniego*<br/>
Ostatni element w sekwencji obiektów, który jest używany do inicjowania bieżącego VectorView. Typ `last` jest przekazywana za pomocą *doskonałego przekazywania*. Aby uzyskać więcej informacji, zobacz [rvalue Reference deklarator:  &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)<br/>
[Tworzenie składników środowisko wykonawcze systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
