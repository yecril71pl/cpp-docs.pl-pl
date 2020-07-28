---
title: ComPtr — Klasa
ms.date: 06/02/2020
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
- client/Microsoft::WRL::ComPtr::As
- client/Microsoft::WRL::ComPtr::AsIID
- client/Microsoft::WRL::ComPtr::AsWeak
- client/Microsoft::WRL::ComPtr::Attach
- client/Microsoft::WRL::ComPtr::ComPtr
- client/Microsoft::WRL::ComPtr::CopyTo
- client/Microsoft::WRL::ComPtr::Detach
- client/Microsoft::WRL::ComPtr::Get
- client/Microsoft::WRL::ComPtr::GetAddressOf
- client/Microsoft::WRL::ComPtr::InternalAddRef
- client/Microsoft::WRL::ComPtr::InternalRelease
- client/Microsoft::WRL::ComPtr::operator&
- client/Microsoft::WRL::ComPtr::operator->
- client/Microsoft::WRL::ComPtr::operator=
- client/Microsoft::WRL::ComPtr::operator==
- client/Microsoft::WRL::ComPtr::operator!=
- client/Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType
- client/Microsoft::WRL::ComPtr::ptr_
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
- client/Microsoft::WRL::ComPtr::Reset
- client/Microsoft::WRL::ComPtr::Swap
- client/Microsoft::WRL::ComPtr::~ComPtr
helpviewer_keywords:
- Microsoft::WRL::ComPtr class
- Microsoft::WRL::ComPtr::As method
- Microsoft::WRL::ComPtr::AsIID method
- Microsoft::WRL::ComPtr::AsWeak method
- Microsoft::WRL::ComPtr::Attach method
- Microsoft::WRL::ComPtr::ComPtr, constructor
- Microsoft::WRL::ComPtr::CopyTo method
- Microsoft::WRL::ComPtr::Detach method
- Microsoft::WRL::ComPtr::Get method
- Microsoft::WRL::ComPtr::GetAddressOf method
- Microsoft::WRL::ComPtr::InternalAddRef method
- Microsoft::WRL::ComPtr::InternalRelease method
- Microsoft::WRL::ComPtr::operator& operator
- Microsoft::WRL::ComPtr::operator-> operator
- Microsoft::WRL::ComPtr::operator= operator
- Microsoft::WRL::ComPtr::operator== operator
- Microsoft::WRL::ComPtr::operator!= operator
- Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType operator
- Microsoft::WRL::ComPtr::ptr_ data member
- Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf method
- Microsoft::WRL::ComPtr::Reset method
- Microsoft::WRL::ComPtr::Swap method
- Microsoft::WRL::ComPtr::~ComPtr, destructor
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
ms.openlocfilehash: 4f9462ca15f5db5c3f8c0de88ce5a76b142065b4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220551"
---
# <a name="comptr-class"></a>ComPtr — Klasa

Tworzy *inteligentny wskaźnik* typu, który reprezentuje interfejs określony przez parametr szablonu. `ComPtr`automatycznie utrzymuje liczbę odwołań dla wskaźnika źródłowego i zwalnia interfejs, gdy liczba odwołań spadnie do zera.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Interfejs, który `ComPtr` reprezentuje.

*U*<br/>
Klasa, do której jest obecny `ComPtr` obiekt zaprzyjaźniony. (Szablon, który używa tego parametru jest chroniony).

## <a name="remarks"></a>Uwagi

`ComPtr<>`deklaruje typ, który reprezentuje wskaźnik podstawowego interfejsu. Użyj, `ComPtr<>` Aby zadeklarować zmienną, a następnie użyć operatora dostępu do elementu członkowskiego () ze strzałką, `->` Aby uzyskać dostęp do funkcji składowej interfejsu.

Aby uzyskać więcej informacji o inteligentnych wskaźnikach, zobacz podsekcję "inteligentne wskaźniki COM" w artykule [dotyczącym tworzenia kodu com](/windows/win32/LearnWin32/com-coding-practices) .

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa            | Opis
--------------- | ---------------------------------------------------------------
`InterfaceType` | Synonim dla typu określonego przez parametr *T* Template.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                             | Opis
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr:: ComPtr](#comptr)        | Inicjuje nowe wystąpienie klasy `ComPtr`. Przeciążenia zapewniają konstruktory domyślne, kopiowanie, przenoszenie i konwersja.
[ComPtr:: ~ ComPtr](#tilde-comptr) | Deinicjalizuje wystąpienie `ComPtr` .

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                      | Opis
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:: as](#as)                                         | Zwraca `ComPtr` obiekt, który reprezentuje interfejs identyfikowany przez określony parametr szablonu.
[ComPtr:: AsIID —](#asiid)                                   | Zwraca `ComPtr` obiekt, który reprezentuje interfejs identyfikowany przez określony identyfikator interfejsu.
[ComPtr:: AsWeak —](#asweak)                                 | Pobiera słabe odwołanie do bieżącego obiektu.
[ComPtr:: Attach](#attach)                                 | Kojarzy to `ComPtr` z typem interfejsu określonym przez bieżący parametr typu szablonu.
[ComPtr:: CopyTo](#copyto)                                 | Kopiuje bieżący lub określony interfejs skojarzony z tym `ComPtr` do określonego wskaźnika danych wyjściowych.
[ComPtr::D etach](#detach)                                 | Usuwa skojarzenie `ComPtr` z interfejsem, który reprezentuje.
[ComPtr:: Get](#get)                                       | Pobiera wskaźnik do interfejsu, który jest skojarzony z tym `ComPtr` .
[ComPtr:: GetAddressOf](#getaddressof)                     | Pobiera adres [ptr_](#ptr) elementu członkowskiego danych, który zawiera wskaźnik do interfejsu reprezentowanego przez ten element `ComPtr` .
[ComPtr:: ReleaseAndGetAddressOf —](#releaseandgetaddressof) | Zwalnia interfejs skojarzony z tym `ComPtr` , a następnie pobiera adres [ptr_](#ptr) elementu członkowskiego danych, który zawiera wskaźnik do wydanego interfejsu.
[ComPtr::Reset](#reset)                                   | Zwalnia interfejs skojarzony z tym `ComPtr` i zwraca nową liczbę odwołań.
[ComPtr:: swap](#swap)                                     | Wymienia interfejs zarządzany przez bieżącą `ComPtr` z interfejsem zarządzanym przez określony `ComPtr` .

### <a name="protected-methods"></a>Metody chronione

Nazwa                                        | Opis
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr:: InternalAddRef —](#internaladdref)   | Zwiększa liczbę odwołań do interfejsu skojarzonego z tym `ComPtr` .
[ComPtr:: InternalRelease —](#internalrelease) | Wykonuje operację wydania modelu COM na interfejsie skojarzonym z tym elementem `ComPtr` .

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                                                           | Opis
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr:: operator&](#operator-ampersand)                                                       | Pobiera adres bieżącego `ComPtr` .
[ComPtr:: operator->](#operator-arrow)                                                          | Pobiera wskaźnik do typu określonego przez bieżący parametr szablonu.
[ComPtr:: operator =](#operator-assign)                                                          | Przypisuje wartość do bieżącej `ComPtr` .
[ComPtr:: operator = =](#operator-equality)                                                       | Wskazuje, czy dwa `ComPtr` obiekty są równe.
[ComPtr:: operator! =](#operator-inequality)                                                     | Wskazuje, czy dwa `ComPtr` obiekty nie są równe.
[ComPtr:: operator Microsoft:: WRL::D etails:: BoolType](#operator-microsoft-wrl-details-booltype) | Wskazuje, czy `ComPtr` zarządza okresem istnienia obiektu w interfejsie.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                 | Opis
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::p tr_](#ptr) | Zawiera wskaźnik do interfejsu, który jest skojarzony z i zarządzany przez ten obiekt `ComPtr` .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Client. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>ComPtr:: ~ ComPtr

Deinicjalizuje wystąpienie `ComPtr` .

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>ComPtr:: as

Zwraca `ComPtr` obiekt, który reprezentuje interfejs identyfikowany przez określony parametr szablonu.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>Parametry

*U*<br/>
Interfejs, który ma być reprezentowany przez parametr *p*.

*St*<br/>
`ComPtr`Obiekt, który reprezentuje interfejs określony przez parametr *U*. Parametr *p* nie może odwoływać się do bieżącego `ComPtr` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy szablon jest formularzem, którego należy użyć w kodzie. Drugi szablon jest wewnętrzną specjalizacją pomocnika. Obsługuje ona funkcje języka C++, takie jak słowo kluczowe odejmowania [autotype.](../../cpp/auto-cpp.md)

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

## <a name="comptrasiid"></a><a name="asiid"></a>ComPtr:: AsIID —

Zwraca `ComPtr` obiekt, który reprezentuje interfejs identyfikowany przez określony identyfikator interfejsu.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identyfikator interfejsu.

*St*<br/>
Jeśli obiekt ma interfejs, którego identyfikator jest równa *riid*, pośredniego wskaźnika do interfejsu określonego przez parametr *riid* . W przeciwnym razie wskaźnik do `IUnknown` .

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

## <a name="comptrasweak"></a><a name="asweak"></a>ComPtr:: AsWeak —

Pobiera słabe odwołanie do bieżącego obiektu.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Parametry

*pWeakRef*<br/>
Po zakończeniu tej operacji wskaźnik do słabego obiektu referencyjnego.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

## <a name="comptrattach"></a><a name="attach"></a>ComPtr:: Attach

Kojarzy to `ComPtr` z typem interfejsu określonym przez bieżący parametr typu szablonu.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Typ interfejsu.

## <a name="comptrcomptr"></a><a name="comptr"></a>ComPtr:: ComPtr

Inicjuje nowe wystąpienie klasy `ComPtr`. Przeciążenia zapewniają konstruktory domyślne, kopiowanie, przenoszenie i konwersja.

```cpp
WRL_NOTHROW ComPtr();

WRL_NOTHROW ComPtr(
   decltype(__nullptr)
);

template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);

WRL_NOTHROW ComPtr(
   const ComPtr& other
);

template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);

WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);

template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other, typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);
```

### <a name="parameters"></a>Parametry

*U*<br/>
Typ *drugiego* parametru.

*różnych*<br/>
Obiekt typu *U*.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor jest konstruktorem domyślnym, który niejawnie tworzy pusty obiekt. Drugi Konstruktor Określa [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), który jawnie tworzy pusty obiekt.

Trzeci Konstruktor tworzy obiekt z obiektu określonego przez wskaźnik. ComPtr jest teraz właścicielem wskazanej pamięci i utrzymuje do niej licznik odwołań.

Czwarty i piąty konstruktory to konstruktory kopiujące. Piąty Konstruktor kopiuje obiekt, jeśli jest konwertowany na bieżący typ.

Szóste i siódme konstruktory są konstruktorami przenoszenia. Siódmy Konstruktor przenosi obiekt, jeśli jest konwertowany na bieżący typ.

## <a name="comptrcopyto"></a><a name="copyto"></a>ComPtr:: CopyTo

Kopiuje bieżący lub określony interfejs skojarzony z tym `ComPtr` do określonego wskaźnika.

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>Parametry

*U*<br/>
Nazwa typu.

*ptr*<br/>
Po zakończeniu tej operacji wskaźnik do żądanego interfejsu.

*riid*<br/>
Identyfikator interfejsu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje dlaczego niejawna `QueryInterface` operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja zwraca kopię wskaźnika do interfejsu skojarzonego z tym obiektem `ComPtr` . Ta funkcja zawsze zwraca S_OK.

Druga funkcja wykonuje `QueryInterface` operację na interfejsie skojarzonym z tym `ComPtr` dla interfejsu określonego przez parametr *riid* .

Trzecia funkcja wykonuje `QueryInterface` operację na interfejsie skojarzonym z tym `ComPtr` dla podstawowego interfejsu *U* .

## <a name="comptrdetach"></a><a name="detach"></a>ComPtr::D etach

`ComPtr`Usuwa obiekt z interfejsu, który reprezentuje.

```cpp
T* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który został reprezentowany przez ten `ComPtr` obiekt.

## <a name="comptrget"></a><a name="get"></a>ComPtr:: Get

Pobiera wskaźnik do interfejsu, który jest skojarzony z tym `ComPtr` .

```cpp
T* Get() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który jest skojarzony z tym elementem `ComPtr` .

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>ComPtr:: GetAddressOf

Pobiera adres [ptr_](#ptr) elementu członkowskiego danych, który zawiera wskaźnik do interfejsu reprezentowanego przez ten element `ComPtr` .

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Adres zmiennej.

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>ComPtr:: InternalAddRef —

Zwiększa liczbę odwołań do interfejsu skojarzonego z tym `ComPtr` .

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Uwagi

Ta metoda jest chroniona.

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>ComPtr:: InternalRelease —

Wykonuje operację wydania modelu COM na interfejsie skojarzonym z tym elementem `ComPtr` .

```cpp
unsigned long InternalRelease();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest chroniona.

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>ComPtr:: operator&amp;

Zwalnia interfejs skojarzony z tym `ComPtr` obiektem, a następnie pobiera adres `ComPtr` obiektu.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Wartość zwracana

Słabe odwołanie do bieżącego elementu `ComPtr` .

### <a name="remarks"></a>Uwagi

Ta metoda różni się od [ComPtr:: GetAddressOf](#getaddressof) w tym metodzie, która zwalnia odwołanie do wskaźnika interfejsu. Użyj `ComPtr::GetAddressOf` , gdy wymagany jest adres wskaźnika interfejsu, ale nie chcesz go zwolnić.

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>ComPtr:: operator-&gt;

Pobiera wskaźnik do typu określonego przez bieżący parametr szablonu.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do typu określonego przez nazwę bieżącego typu szablonu.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika usuwa niepotrzebne obciążenie spowodowane przez użycie makra STDMETHOD. Ta funkcja tworzy `IUnknown` typy **`private`** zamiast **`virtual`** .

## <a name="comptroperator"></a><a name="operator-assign"></a>ComPtr:: operator =

Przypisuje wartość do bieżącej `ComPtr` .

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>Parametry

*U*<br/>
Klasa.

*różnych*<br/>
Wskaźnikiem, odwołaniem lub rvalue odwołaniem do typu lub innego `ComPtr` .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego elementu `ComPtr` .

### <a name="remarks"></a>Uwagi

Pierwsza wersja tego operatora przypisuje pustą wartość do bieżącej `ComPtr` .

W drugiej wersji, jeśli wskaźnik przypisywania interfejsu nie jest taki sam jak bieżący `ComPtr` wskaźnik interfejsu, drugi wskaźnik interfejsu jest przypisany do bieżącego `ComPtr` .

W trzeciej wersji wskaźnik przypisywania interfejsu jest przypisany do bieżącego `ComPtr` .

W czwartej wersji, jeśli wskaźnik interfejsu przypisanej wartości nie jest taki sam jak bieżący `ComPtr` wskaźnik interfejsu, drugi wskaźnik interfejsu jest przypisany do bieżącego `ComPtr` .

Piąta wersja jest operatorem kopiowania; odwołanie do elementu `ComPtr` jest przypisane do bieżącego `ComPtr` .

Szósta wersja jest operatorem kopiowania, który używa semantyki przenoszenia; odwołanie rvalue do elementu `ComPtr` if dowolnego typu jest rzutowane statyczne, a następnie przypisane do bieżącego `ComPtr` .

Siódma wersja jest operatorem kopiowania, który używa semantyki przenoszenia; odwołanie rvalue do `ComPtr` typu *U* jest statyczne rzutowanie, a następnie przypisane do bieżącego elementu `ComPtr` .

## <a name="comptroperator"></a><a name="operator-equality"></a>ComPtr:: operator = =

Wskazuje, czy dwa `ComPtr` obiekty są równe.

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Odwołanie do `ComPtr` obiektu.

*b*<br/>
Odwołanie do innego `ComPtr` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator daje **`true`** , że obiekt *a* jest równy obiektowi *b*; w przeciwnym razie **`false`** .

Drugi i trzeci operator **`true`** uzyskują wartość, jeśli obiekt *a* jest równy **`nullptr`** ; w przeciwnym razie **`false`** .

## <a name="comptroperator"></a><a name="operator-inequality"></a>ComPtr:: operator! =

Wskazuje, czy dwa `ComPtr` obiekty nie są równe.

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Odwołanie do `ComPtr` obiektu.

*b*<br/>
Odwołanie do innego `ComPtr` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator daje **`true`** , że obiekt *a* nie jest równy obiektowi *b*; w przeciwnym razie **`false`** .

Drugi i trzeci operator **`true`** uzyskują wartość, jeśli obiekt *a* nie jest równy **`nullptr`** ; w przeciwnym razie **`false`** .

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>ComPtr:: operator Microsoft:: WRL::D etails:: BoolType

Wskazuje, czy `ComPtr` zarządza okresem istnienia obiektu w interfejsie.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli interfejs jest skojarzony z tym `ComPtr` , adresem elementu członkowskiego danych [BoolStruct:: member](boolstruct-structure.md#member) ; w przeciwnym razie, **`nullptr`** .

## <a name="comptrptr_"></a><a name="ptr"></a>ComPtr::p tr_

Zawiera wskaźnik do interfejsu, który jest skojarzony z i zarządzany przez ten obiekt `ComPtr` .

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Uwagi

`ptr_`to wewnętrzny, chroniony element członkowski danych.

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtr:: ReleaseAndGetAddressOf —

Zwalnia interfejs skojarzony z tym `ComPtr` , a następnie pobiera adres [ptr_](#ptr) elementu członkowskiego danych, który zawiera wskaźnik do wydanego interfejsu.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Adres elementu członkowskiego danych [ptr_](#ptr) `ComPtr` .

## <a name="comptrreset"></a><a name="reset"></a>ComPtr:: Reset

Zwalnia interfejs skojarzony z tym `ComPtr` i zwraca nową liczbę odwołań.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Wartość zwracana

Liczba odwołań pozostałych do bazowego interfejsu (jeśli istnieją).

## <a name="comptrswap"></a><a name="swap"></a>ComPtr:: swap

Wymienia interfejs zarządzany przez bieżącą `ComPtr` z interfejsem zarządzanym przez określony `ComPtr` .

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Parametry

*®*<br/>
Klasa `ComPtr`.
