---
title: Platform::Collections::Vector, klasa
ms.date: 12/04/2019
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
ms.openlocfilehash: 60c82a113bc19e9652af8c1ad531e1c479077f20
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032125"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector, klasa

Reprezentuje sekwencyjnej kolekcji obiektów, które mogą być indywidualnie dostępne przez indeks. Implementuje [system Windows::Foundation::Collections::IObservableVector,](/uwp/api/windows.foundation.collections.iobservablevector-1) aby pomóc w [wiązaniu danych](/windows/uwp/data-binding/data-binding-in-depth)XAML .

## <a name="syntax"></a>Składnia

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ elementów zawartych w obiekcie Vector.

*E*<br/>
Określa predykat binarny do testowania równości z wartościami typu *T*. Wartością domyślną jest `std::equal_to<T>`.

### <a name="remarks"></a>Uwagi

Dozwolone typy to:

1. liczby całkowite

1. klasa interfejsu^

1. publiczna klasa ref^

1. struktura wartości

1. klasa wyliczenia publicznego

Klasa **Vector** jest implementacją betonu języka C++ interfejsu [systemu Windows::Foundation::Collections::IVector.](/uwp/api/windows.foundation.collections.ivector-1)

Jeśli spróbujesz użyć typu **Vector** w publicznej wartości zwracania lub parametru, błąd kompilatora C3986 jest wywoływany. Błąd można naprawić, zmieniając parametr lub zwraca typ wartości do [systemu Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1). Aby uzyskać więcej informacji, zobacz [Kolekcje (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Wektor::Wektor](#ctor)|Inicjuje nowe wystąpienie klasy Wektor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Wektor::Dołącz](#append)|Wstawia określony element po ostatnim elemencie w bieżącym wektorze.|
|[Wektor::Wyczyść](#clear)|Usuwa wszystkie elementy w bieżącym wektorze.|
|[Wektor::Najpierw](#first)|Zwraca iterator, który określa pierwszy element wektora.|
|[Wektor::GetAt](#getat)|Pobiera element bieżącego Wektora, który jest identifed przez określony indeks.|
|[Wektor::GetMany](#getmany)|Pobiera sekwencję elementów z bieżącego wektora, począwszy od określonego indeksu.|
|[Wektor::GetView](#getview)|Zwraca widok tylko do odczytu wektora; oznacza to, że [platforma::Kolekcje::VectorView](../cppcx/platform-collections-vectorview-class.md).|
|[Wektor::IndexOf](#indexof)|Wyszukuje określony element w bieżącym vector, a jeśli zostanie znaleziony, zwraca indeks elementu.|
|[Wektor::Wstawianie](#insertat)|Wstawia określony element do bieżącego wektora w elemencie identyfikowanym przez określony indeks.|
|[Wektor::ReplaceAll](#replaceall)|Usuwa elementy w bieżącym Vector, a następnie wstawia elementy z określonej tablicy.|
|[Wektor::RemoveAt](#removeat)|Usuwa element identyfikowany przez określony indeks z bieżącego wektora.|
|[Wektor::RemoveAtEnd](#removeatend)|Usuwa element na końcu bieżącego wektora.|
|[Wektor::SetAt](#setat)|Przypisuje określoną wartość do elementu w bieżącym Wektor, który jest identyfikowany przez określony indeks.|
|[Wektor::Rozmiar](#size)|Zwraca liczbę elementów w bieżącym obiekcie Vector.|

### <a name="events"></a>Zdarzenia

|||
|-|-|
|Nazwa|Opis|
|zdarzenie [Windows::Foundation::Collection::VectorChangedEventHandler\<T>^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1)|Występuje, gdy zmienia się wektor.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Vector`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Obszar nazw:** Platforma::Kolekcje

## <a name="vectorappend-method"></a><a name="append"></a>Wektor::Metoda dołączania

Wstawia określony element po ostatnim elemencie w bieżącym wektorze.

### <a name="syntax"></a>Składnia

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Element do wstawienia do wektora. Typ *towaru* jest definiowany przez nazwa typu *T.*

## <a name="vectorclear-method"></a><a name="clear"></a>Wektor::Clear Metoda

Usuwa wszystkie elementy w bieżącym wektorze.

### <a name="syntax"></a>Składnia

```cpp
virtual void Clear();
```

## <a name="vectorfirst-method"></a><a name="first"></a>Wektor::Pierwsza metoda

Zwraca iterator, który wskazuje pierwszy element wektora.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który wskazuje na pierwszy element wektora.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwróconego przez First() jest przypisanie wartości zwracanej do zmiennej zadeklarowanej za pomocą słowa kluczowego **automatycznego** potrącenia typu. Na przykład `auto x = myVector->First();`. Ten iterator zna długość kolekcji.

Jeśli potrzebujesz pary iteratorów do przekazania do funkcji STL, użyj bezpłatnych funkcji [Windows::Foundation::Collections::begin](../cppcx/begin-function.md) i [Windows::Foundation::Collections::end](../cppcx/end-function.md)

## <a name="vectorgetat-method"></a><a name="getat"></a>Wektor::Metoda GetAt

Pobiera element bieżącego Wektora, który jest identifed przez określony indeks.

### <a name="syntax"></a>Składnia

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Zero-based, niepodpisane liczby całkowitej, która określa określony element w Vector obiektu.

### <a name="return-value"></a>Wartość zwracana

Element określony przez parametr *indeksu.* Typ elementu jest definiowany przez wartość typu *T.*

## <a name="vectorgetmany-method"></a><a name="getmany"></a>Wektor::Metoda GetMany

Pobiera sekwencję elementów z bieżącego wektora, począwszy od określonego indeksu i kopiuje je do tablicy przydzielonej przez wywołującego.

### <a name="syntax"></a>Składnia

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Parametry

*Startindex*<br/>
Indeks od zera początku elementów do pobrania.

*Dest*<br/>
Tablica elementów przydzielonych przez wywołującego, które rozpoczynają się od elementu określonego przez *startIndex* i kończą na ostatnim elemencie wektora.

### <a name="return-value"></a>Wartość zwracana

Liczba pobranych elementów.

### <a name="remarks"></a>Uwagi

Ta funkcja nie jest przeznaczona do użytku bezpośrednio przez kod klienta. Jest on używany wewnętrznie w [funkcji to_vector,](../cppcx/to-vector-function.md) aby umożliwić wydajną konwersję intances platformy::Vector do std::vector wystąpień.

## <a name="vectorgetview-method"></a><a name="getview"></a>Wektor::Metoda GetView

Zwraca widok tylko do odczytu wektora; oznacza to, że IVectorView.

### <a name="syntax"></a>Składnia

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt IVectorView.

## <a name="vectorindexof-method"></a><a name="indexof"></a>Wektor::Metoda IndexOf

Wyszukuje określony element w bieżącym vector, a jeśli zostanie znaleziony, zwraca indeks elementu.

### <a name="syntax"></a>Składnia

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Element do znalezienia.

*Indeks*<br/>
Indeks od zera towaru, jeśli zostanie znaleziona *wartość* parametru; w przeciwnym razie 0.

Parametr *indeksu* wynosi 0, jeśli element jest pierwszym elementem wektora lub nie znaleziono elementu. Jeśli wartość zwracana jest **true**, element został znaleziony i jest pierwszym elementem; w przeciwnym razie nie znaleziono elementu.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli zostanie znaleziony określony element; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

IndexOf używa std::find_if, aby znaleźć element. Typy elementów niestandardowych należy zatem przeciążyć == i != operator w celu włączenia porównań równości, które find_if wymaga.

## <a name="vectorinsertat-method"></a><a name="insertat"></a>Wektor::Metoda Wstawiania

Wstawia określony element do bieżącego wektora w elemencie identyfikowanym przez określony indeks.

### <a name="syntax"></a>Składnia

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Zero-based, niepodpisane liczby całkowitej, która określa określony element w Vector obiektu.

*Element*<br/>
Element do wstawienia do wektora w elemencie określonym przez *indeks*. Typ *towaru* jest definiowany przez nazwa typu *T.*

## <a name="vectorremoveat-method"></a><a name="removeat"></a>Wektor::Metoda RemoveAt

Usuwa element identyfikowany przez określony indeks z bieżącego wektora.

### <a name="syntax"></a>Składnia

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Zero-based, niepodpisane liczby całkowitej, która określa określony element w Vector obiektu.

## <a name="vectorremoveatend-method"></a><a name="removeatend"></a>Wektor::RemoveAtEnd Metoda

Usuwa element na końcu bieżącego wektora.

### <a name="syntax"></a>Składnia

```cpp
virtual void RemoveAtEnd();
```

## <a name="vectorreplaceall-method"></a><a name="replaceall"></a>Wektor::ReplaceAll Metoda

Usuwa elementy w bieżącym Vector, a następnie wstawia elementy z określonej tablicy.

### <a name="syntax"></a>Składnia

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Parametry

*Arr*<br/>
Tablica obiektów, których typ jest zdefiniowany przez wartość typu *T.*

## <a name="vectorsetat-method"></a><a name="setat"></a>Wektor::Metoda SetAt

Przypisuje określoną wartość do elementu w bieżącym Wektor, który jest identyfikowany przez określony indeks.

### <a name="syntax"></a>Składnia

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Zero-based, niepodpisane liczby całkowitej, która określa określony element w Vector obiektu.

*Element*<br/>
Wartość do przypisania do określonego elementu. Typ *towaru* jest definiowany przez nazwa typu *T.*

## <a name="vectorsize-method"></a><a name="size"></a>Wektor::Metoda rozmiaru

Zwraca liczbę elementów w bieżącym obiekcie Vector.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w bieżącym wektorze.

## <a name="vectorvector-constructor"></a><a name="ctor"></a>Wektor::Konstruktor wektorowy

Inicjuje nowe wystąpienie klasy Wektor.

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

*A*<br/>
A [std::array,](../standard-library/array-class-stl.md) który będzie używany do inicjowania Wektora.

*Arr*<br/>
A [Platform::Array,](../cppcx/platform-array-class.md) który będzie używany do inicjowania Wektora.

*Init*<br/>
Typ kolekcji obiektów, który jest używany do inicjowania bieżącego wektora.

*Il*<br/>
A [std::initializer_list](../standard-library/initializer-list-class.md) obiektów typu *T,* które będą używane do inicjowania wektora.

*N*<br/>
Liczba elementów w kolekcji obiektów, która jest używana do inicjowania bieżącego Wektora.

*Rozmiar*<br/>
Liczba elementów wektora.

*value*<br/>
Wartość, która jest używana do inicjowania każdego elementu w bieżącym Vector.

*v*<br/>
[Wartość Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::vector,](../standard-library/vector-class.md) który jest używany do inicjowania bieżącego wektora.

*Ptr*<br/>
Wskaźnik do, `std::vector` który jest używany do inicjowania bieżącego Wektora.

*Pierwszym*<br/>
Pierwszy element w sekwencji obiektów, które są używane do inicjowania bieżącego Wektora. Typ *pierwszego* jest przekazywany za pomocą *doskonałego przekazywania.* Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*Ostatnio*<br/>
Ostatni element w sekwencji obiektów, które są używane do inicjowania bieżącego Wektora. Typ *ostatniego* jest przekazywany za pomocą *doskonałego przekazywania.* Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Zobacz też

[Kolekcje (C++/CX)](collections-c-cx.md)<br/>
[Obszar nazw platformy](platform-namespace-c-cx.md)<br/>
[Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
