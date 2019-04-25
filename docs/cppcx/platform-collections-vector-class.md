---
title: 'Platform::Collections:: Vector, klasa'
ms.date: 12/30/2016
ms.topic: reference
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
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
ms.openlocfilehash: 5466f1d1c8987724aa0768cd8915e06b62b031ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161644"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections:: Vector, klasa

Reprezentuje sekwencyjną kolekcją obiektów, które mogą być indywidualnie uzyskać dostęp przez indeks.

## <a name="syntax"></a>Składnia

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ elementów znajdujących się w obiektu wektora.

*E*<br/>
Określa binarny predykat równości z wartościami typu testowania *T*. Wartość domyślna to `std::equal_to<T>`.

### <a name="remarks"></a>Uwagi

Dozwolone typy to:

1. liczby całkowite

1. Klasa interfejsu ^

1. Klasa ref publicznych ^

1. Struktura wartości

1. Klasa wyliczeniowa publiczne

**Wektor** klasa jest C++ wykonanie [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) interfejsu.

Jeśli spróbujesz użyć **wektor** wpisz publiczny wartość zwracana lub parametr, błąd kompilatora C3986 jest wywoływane. Można naprawić ten błąd, zmieniając parametr lub zwracany typ wartości do [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_). Aby uzyskać więcej informacji, zobacz [kolekcji (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Vector::Vector](#ctor)|Inicjuje nowe wystąpienie klasy wektora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Vector::append](#append)|Wstawia określony element po ostatnim elemencie w zakresie bieżącego ataku.|
|[Vector::Clear](#clear)|Usuwa wszystkie elementy w bieżącym wektora.|
|[Vector::First](#first)|Zwraca iterator, który określa pierwszego elementu w wektorze.|
|[Vector::GetAt](#getat)|Pobiera element bieżącego wektor, który jest identyfikować przez określony indeks.|
|[Vector::GetMany](#getmany)|Pobiera sekwencję elementów z bieżącego wektora, rozpoczynając od określonego indeksu.|
|[Vector::GetView](#getview)|Zwraca wektor; widok tylko do odczytu oznacza to, że [platform::Collections:: vectorview](../cppcx/platform-collections-vectorview-class.md).|
|[Vector::IndexOf](#indexof)|Wyszukuje określony element w zakresie bieżącego ataku i, jeśli znaleziono zwraca indeks elementu.|
|[Vector::InsertAt](#insertat)|Wstawia określony element do bieżącego wektora po elemencie identyfikowane przez określony indeks.|
|[Vector::ReplaceAll](#replaceall)|Usuwa elementy w zakresie bieżącego ataku i wstawia elementy z określonej tablicy.|
|[Vector::RemoveAt](#removeat)|Usuwa element identyfikowane przez określony indeks z bieżącym wektora.|
|[Vector::RemoveAtEnd](#removeatend)|Usuwa element na końcu bieżącego wektora.|
|[Vector::SetAt](#setat)|Przypisuje wartość określonego elementu w bieżącym wektor, który jest identyfikowany przez określony indeks.|
|[Vector::Size](#size)|Zwraca liczbę elementów w bieżącym obiekcie wektora.|

### <a name="events"></a>Zdarzenia

|||
|-|-|
|Nazwa|Opis|
|event [Windows::Foundation::Collection::VectorChangedEventHandler\<T>^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|Występuje po zmianie wektora.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Vector`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Platform::Collections

## <a name="append"></a>  Metoda Vector::append

Wstawia określony element po ostatnim elemencie w zakresie bieżącego ataku.

### <a name="syntax"></a>Składnia

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Element do wstawienia do wektora. Typ *elementu* jest definiowany przez *T* typename.

## <a name="clear"></a>  Vector::Clear — metoda

Usuwa wszystkie elementy w bieżącym wektora.

### <a name="syntax"></a>Składnia

```cpp
virtual void Clear();
```

## <a name="first"></a>  Metoda Vector::First

Zwraca iterator odwołujący się do pierwszego elementu w wektorze.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który wskazuje na pierwszy element w wektorze.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratorów zwróconych przez First() jest przypisanie zwracana wartość do zmiennej, która jest zadeklarowana za pomocą **automatycznie** słowem kluczowym dedukcji typu. Na przykład `auto x = myVector->First();`. Ta iteratora wie, długość kolekcji.

Para iteratorów do przekazania do funkcji STL, użyj bezpłatnych funkcji [Windows::Foundation:: Collections:: rozpocząć](../cppcx/begin-function.md) i [Windows::Foundation::Collections::end](../cppcx/end-function.md)

## <a name="getat"></a>  Metoda Vector::GetAt

Pobiera element bieżącego wektor, który jest identyfikować przez określony indeks.

### <a name="syntax"></a>Składnia

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Liczony od zera, nieoznaczona liczba całkowita określająca konkretnego elementu w obiekcie wektora.

### <a name="return-value"></a>Wartość zwracana

Określony przez element *indeksu* parametru. Typ elementu jest definiowany przez *T* typename.

## <a name="getmany"></a>  Metoda Vector::GetMany

Pobiera sekwencję elementów z bieżącego wektora, zaczynając od określonego indeksu i kopiuje je do tablica przydzielana przez obiekt wywołujący.

### <a name="syntax"></a>Składnia

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Parametry

*startIndex*<br/>
Liczony od zera indeks początku elementów do pobrania.

*dest*<br/>
Tablica przydzielana przez obiekt wywołujący elementów, które zaczynają się na określony przez element *startIndex* i końcowy z ostatniego elementu w wektorze.

### <a name="return-value"></a>Wartość zwracana

Pobrać liczbę elementów.

### <a name="remarks"></a>Uwagi

Ta funkcja nie jest przeznaczony do użycia bezpośrednio przez kod klienta. Jest używana wewnętrznie w [to_vector, funkcja](../cppcx/to-vector-function.md) umożliwiające wydajne konwersja wystąpienia Platform::Vector std::vector wystąpień.

## <a name="getview"></a>  Metoda Vector::GetView

Zwraca wektor; widok tylko do odczytu oznacza to, że IVectorView.

### <a name="syntax"></a>Składnia

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, który IVectorView.

## <a name="indexof"></a>  Metoda Vector::IndexOf

Wyszukuje określony element w zakresie bieżącego ataku i, jeśli znaleziono zwraca indeks elementu.

### <a name="syntax"></a>Składnia

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Element do znalezienia.

*index*<br/>
Liczony od zera indeks elementu Jeśli parametr *wartość* jest; w przeciwnym razie 0.

*Indeksu* parametru to 0, jeśli element jest pierwszy element wektora lub element nie został znaleziony. Jeśli wartość zwracana jest **true**, element został odnaleziony i jest pierwszy element; w przeciwnym razie nie znaleziono elementu.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli określony element; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

IndexOf używa std::find_if Aby znaleźć element. Typy elementu niestandardowego, w związku z tym powinien przeciążać == i! = — operator w celu umożliwienia równości wymaga tego find_if porównania.

##  <a name="insertat"></a>  Metoda Vector::InsertAt

Wstawia określony element do bieżącego wektora po elemencie identyfikowane przez określony indeks.

### <a name="syntax"></a>Składnia

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Parametry

*index*<br/>
Liczony od zera, nieoznaczona liczba całkowita określająca konkretnego elementu w obiekcie wektora.

*item*<br/>
Element do wstawienia do wektora po określony przez element *indeksu*. Typ *elementu* jest definiowany przez *T* typename.

## <a name="removeat"></a>  Metoda Vector::RemoveAt

Usuwa element identyfikowane przez określony indeks z bieżącym wektora.

### <a name="syntax"></a>Składnia

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Liczony od zera, nieoznaczona liczba całkowita określająca konkretnego elementu w obiekcie wektora.

## <a name="removeatend"></a>  Metoda Vector::RemoveAtEnd

Usuwa element na końcu bieżącego wektora.

### <a name="syntax"></a>Składnia

```cpp
virtual void RemoveAtEnd();
```

## <a name="replaceall"></a>  Metoda Vector::ReplaceAll

Usuwa elementy w zakresie bieżącego ataku i wstawia elementy z określonej tablicy.

### <a name="syntax"></a>Składnia

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Parametry

*Moduł ARR*<br/>
Użyj tablicy obiektów o tym, którego typ jest zdefiniowany przez *T* typename.

## <a name="setat"></a>  Metoda Vector::SetAt

Przypisuje wartość określonego elementu w bieżącym wektor, który jest identyfikowany przez określony indeks.

### <a name="syntax"></a>Składnia

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Liczony od zera, nieoznaczona liczba całkowita określająca konkretnego elementu w obiekcie wektora.

*item*<br/>
Wartość do przypisania do określonego elementu. Typ *elementu* jest definiowany przez *T* typename.

## <a name="size"></a>  Vector::size — metoda

Zwraca liczbę elementów w bieżącym obiekcie wektora.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w bieżącym wektora.

## <a name="ctor"></a>  Vector::Vector konstruktora

Inicjuje nowe wystąpienie klasy wektora.

### <a name="syntax"></a>Składnia

```cpp
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

*a*<br/>
A [std::array](../standard-library/array-class-stl.md) posłuży inicjują wektor.

*Moduł ARR*<br/>
A [Platform::Array](../cppcx/platform-array-class.md) posłuży inicjują wektor.

*InIt*<br/>
Typ kolekcji obiektów służy do inicjowania bieżącego wektora.

*il*<br/>
A [std::initializer_list](../standard-library/initializer-list-class.md) obiektów typu *T* posłuży inicjują wektor.

*N*<br/>
Liczba elementów w kolekcji obiektów, które służy do inicjowania bieżącego wektora.

*Rozmiar*<br/>
Liczba elementów w wektorze.

*value*<br/>
Wartość, która służy do inicjowania każdego elementu w bieżącym wektora.

*v*<br/>
[Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::vector](../standard-library/vector-class.md) umożliwiający inicjują wektor bieżącego.

*ptr*<br/>
Wskaźnik do `std::vector` umożliwiający inicjują wektor bieżącego.

*pierwszy*<br/>
Pierwszy element w sekwencji obiektów, które są stosowane do inicjalizacji bieżącego wektora. Typ *pierwszy* jest przekazywany przez *doskonała przekazywania*. Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
Ostatniego elementu w sekwencji obiektów, które są stosowane do inicjalizacji bieżącego wektora. Typ *ostatniego* jest przekazywany przez *doskonała przekazywania*. Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Zobacz także

[Namespace platformy](platform-namespace-c-cx.md)<br/>
[Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
