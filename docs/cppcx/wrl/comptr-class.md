---
title: ComPtr — Klasa
ms.date: 07/26/2019
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
ms.openlocfilehash: 889b722c91fd56613c5902eb4ce6439763a49bd9
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606490"
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

`ComPtr<>`deklaruje typ, który reprezentuje wskaźnik podstawowego interfejsu. Użyj `ComPtr<>` , aby zadeklarować zmienną, a następnie użyć operatora dostępu do elementu członkowskiego (`->`) ze strzałką, aby uzyskać dostęp do funkcji składowej interfejsu.

Aby uzyskać więcej informacji o inteligentnych wskaźnikach, zobacz podsekcję "inteligentne wskaźniki COM" w temacie [wskazówki dotyczące kodowania com](/windows/desktop/LearnWin32/com-coding-practices) w bibliotece MSDN.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa            | Opis
--------------- | ---------------------------------------------------------------
`InterfaceType` | Synonim dla typu określonego przez parametr *T* Template.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                             | Opis
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | Aktywuje nowe wystąpienie `ComPtr` klasy. Przeciążenia zapewniają konstruktory domyślne, kopiowanie, przenoszenie i konwersja.
[ComPtr::~ComPtr](#tilde-comptr) | Deinicjalizuje wystąpienie `ComPtr`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                      | Opis
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:: as](#as)                                         | `ComPtr` Zwraca obiekt, który reprezentuje interfejs identyfikowany przez określony parametr szablonu.
[ComPtr:: AsIID —](#asiid)                                   | `ComPtr` Zwraca obiekt, który reprezentuje interfejs identyfikowany przez określony identyfikator interfejsu.
[ComPtr:: AsWeak —](#asweak)                                 | Pobiera słabe odwołanie do bieżącego obiektu.
[ComPtr:: Attach](#attach)                                 | Kojarzy `ComPtr` to z typem interfejsu określonym przez bieżący parametr typu szablonu.
[ComPtr::CopyTo](#copyto)                                 | Kopiuje bieżący lub określony interfejs skojarzony z tym `ComPtr` do określonego wskaźnika danych wyjściowych.
[ComPtr::D etach](#detach)                                 | Usuwa skojarzenie `ComPtr` z interfejsem, który reprezentuje.
[ComPtr:: Get](#get)                                       | Pobiera wskaźnik do interfejsu, który jest skojarzony z tym `ComPtr`.
[ComPtr:: GetAddressOf](#getaddressof)                     | Pobiera adres elementu członkowskiego danych [ptr_](#ptr) , który zawiera wskaźnik do interfejsu reprezentowanego przez ten `ComPtr`element.
[ComPtr:: ReleaseAndGetAddressOf —](#releaseandgetaddressof) | Zwalnia interfejs skojarzony z tym `ComPtr` , a następnie pobiera adres elementu członkowskiego danych [ptr_](#ptr) , który zawiera wskaźnik do wydanego interfejsu.
[ComPtr::Reset](#reset)                                   | Zwalnia wszystkie odwołania dla wskaźnika do interfejsu, który jest skojarzony z tym `ComPtr`.
[ComPtr::Swap](#swap)                                     | Wymienia interfejs zarządzany przez bieżącą `ComPtr` z interfejsem zarządzanym przez określony. `ComPtr`

### <a name="protected-methods"></a>Metody chronione

Nazwa                                        | Opis
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr:: InternalAddRef —](#internaladdref)   | Zwiększa liczbę odwołań do interfejsu skojarzonego z tym `ComPtr`.
[ComPtr:: InternalRelease —](#internalrelease) | Wykonuje operację wydania modelu COM na interfejsie skojarzonym z `ComPtr`tym elementem.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                                                           | Opis
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr:: operator &](#operator-ampersand)                                                       | Pobiera adres bieżącego `ComPtr`.
[ComPtr:: operator->](#operator-arrow)                                                          | Pobiera wskaźnik do typu określonego przez bieżący parametr szablonu.
[ComPtr:: operator =](#operator-assign)                                                          | Przypisuje wartość do bieżącej `ComPtr`.
[ComPtr:: operator = =](#operator-equality)                                                       | Wskazuje, czy `ComPtr` dwa obiekty są równe.
[ComPtr:: operator! =](#operator-inequality)                                                     | Wskazuje, czy `ComPtr` dwa obiekty nie są równe.
[ComPtr:: operator Microsoft:: WRL::D etails:: BoolType](#operator-microsoft-wrl-details-booltype) | Wskazuje, `ComPtr` czy zarządza okresem istnienia obiektu w interfejsie.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                 | Opis
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | Zawiera wskaźnik do interfejsu, który jest skojarzony z i zarządzany przez ten `ComPtr`obiekt.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Client. h

**Obszaru** Microsoft:: WRL

## <a name="tilde-comptr"></a>ComPtr::~ComPtr

Deinicjalizuje wystąpienie `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>ComPtr:: as

`ComPtr` Zwraca obiekt, który reprezentuje interfejs identyfikowany przez określony parametr szablonu.

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

*p*<br/>
Obiekt, który reprezentuje interfejs określony przez parametr *U.* `ComPtr` Parametr *p* nie może odwoływać się do `ComPtr` bieżącego obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy szablon jest formularzem, którego należy użyć w kodzie. Drugi szablon jest wewnętrzną specjalizacją pomocnika, która obsługuje C++ funkcje językowe, takie jak słowo kluczowe potrącenie [typu](../../cpp/auto-cpp.md) autoodejmowanie.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

## <a name="asiid"></a>ComPtr:: AsIID —

`ComPtr` Zwraca obiekt, który reprezentuje interfejs identyfikowany przez określony identyfikator interfejsu.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identyfikator interfejsu.

*p*<br/>
Jeśli obiekt ma interfejs, którego identyfikator jest równa *riid*, pośredniego wskaźnik do interfejsu określonego przez parametr *riid* ; w przeciwnym razie wskaźnik do `IUnknown`.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

## <a name="asweak"></a>ComPtr:: AsWeak —

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

## <a name="attach"></a>ComPtr:: Attach

Kojarzy `ComPtr` to z typem interfejsu określonym przez bieżący parametr typu szablonu.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parametry

*other*<br/>
Typ interfejsu.

## <a name="comptr"></a>ComPtr::ComPtr

Aktywuje nowe wystąpienie `ComPtr` klasy. Przeciążenia zapewniają konstruktory domyślne, kopiowanie, przenoszenie i konwersja.

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

*other*<br/>
Obiekt typu *U*.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor jest konstruktorem domyślnym, który niejawnie tworzy pusty obiekt. Drugi Konstruktor Określa [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), który jawnie tworzy pusty obiekt.

Trzeci Konstruktor tworzy obiekt z obiektu określonego przez wskaźnik. ComPtr jest teraz właścicielem wskazanej pamięci i utrzymuje do niej licznik odwołań.

Czwarty i piąty konstruktory to konstruktory kopiujące. Piąty Konstruktor kopiuje obiekt, jeśli jest konwertowany na bieżący typ.

Szóste i siódme konstruktory są konstruktorami przenoszenia. Siódmy Konstruktor przenosi obiekt, jeśli jest konwertowany na bieżący typ.

## <a name="copyto"></a>ComPtr:: CopyTo

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

Pierwsza funkcja zwraca kopię wskaźnika do interfejsu skojarzonego z tym `ComPtr`obiektem. Ta funkcja zawsze zwraca S_OK.

Druga funkcja wykonuje `QueryInterface` operację na interfejsie skojarzonym z tym `ComPtr` dla interfejsu określonego przez parametr *riid* .

Trzecia funkcja wykonuje `QueryInterface` operację na interfejsie skojarzonym z tym `ComPtr` dla podstawowego interfejsu *U* .

## <a name="detach"></a>ComPtr::D etach

`ComPtr` Usuwa obiekt z interfejsu, który reprezentuje.

```cpp
T* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który został reprezentowany przez ten `ComPtr` obiekt.

## <a name="get"></a>ComPtr:: Get

Pobiera wskaźnik do interfejsu, który jest skojarzony z tym `ComPtr`.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który jest skojarzony z tym `ComPtr`elementem.

## <a name="getaddressof"></a>ComPtr:: GetAddressOf

Pobiera adres elementu członkowskiego danych [ptr_](#ptr) , który zawiera wskaźnik do interfejsu reprezentowanego przez ten `ComPtr`element.

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Adres zmiennej.

## <a name="internaladdref"></a>ComPtr:: InternalAddRef —

Zwiększa liczbę odwołań do interfejsu skojarzonego z tym `ComPtr`.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Uwagi

Ta metoda jest chroniona.

## <a name="internalrelease"></a>ComPtr:: InternalRelease —

Wykonuje operację wydania modelu COM na interfejsie skojarzonym z `ComPtr`tym elementem.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest chroniona.

## <a name="operator-ampersand"></a>ComPtr:: operator&amp;

Zwalnia interfejs skojarzony z tym `ComPtr` obiektem, a następnie pobiera adres `ComPtr` obiektu.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Wartość zwracana

Słabe odwołanie do bieżącego `ComPtr`elementu.

### <a name="remarks"></a>Uwagi

Ta metoda różni się od [ComPtr:: GetAddressOf](#getaddressof) w tym metodzie, która zwalnia odwołanie do wskaźnika interfejsu. Użyj `ComPtr::GetAddressOf` , gdy wymagany jest adres wskaźnika interfejsu, ale nie chcesz go zwolnić.

## <a name="operator-arrow"></a>ComPtr:: operator-&gt;

Pobiera wskaźnik do typu określonego przez bieżący parametr szablonu.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do typu określonego przez nazwę bieżącego typu szablonu.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika usuwa niepotrzebne obciążenie spowodowane przez użycie makra STDMETHOD. Ta funkcja tworzy `IUnknown` typy `private` zamiast `virtual`.

## <a name="operator-assign"></a>ComPtr:: operator =

Przypisuje wartość do bieżącej `ComPtr`.

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

*other*<br/>
Wskaźnikiem, odwołaniem lub rvalue odwołaniem do typu lub innego `ComPtr`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego `ComPtr`elementu.

### <a name="remarks"></a>Uwagi

Pierwsza wersja tego operatora przypisuje pustą wartość do bieżącej `ComPtr`.

W drugiej wersji, jeśli wskaźnik przypisywania interfejsu nie jest taki sam jak bieżący `ComPtr` wskaźnik interfejsu, drugi wskaźnik interfejsu jest przypisany do bieżącego. `ComPtr`

W trzeciej wersji wskaźnik przypisywania interfejsu jest przypisany do bieżącego `ComPtr`.

W czwartej wersji, jeśli wskaźnik interfejsu przypisanej wartości nie jest taki sam jak bieżący `ComPtr` wskaźnik interfejsu, drugi wskaźnik interfejsu jest przypisany do bieżącego. `ComPtr`

Piąta wersja jest operatorem kopiowania; odwołanie do elementu `ComPtr` jest przypisane do bieżącego `ComPtr`.

Szósta wersja jest operatorem kopiowania, który używa semantyki przenoszenia; odwołanie rvalue do elementu `ComPtr` if dowolnego typu jest rzutowane statyczne, a następnie przypisane do bieżącego. `ComPtr`

Siódma wersja jest operatorem kopiowania, który używa semantyki przenoszenia; odwołanie rvalue do typu *U* jest statyczne rzutowanie, a następnie przypisane do bieżącego `ComPtr`elementu. `ComPtr`

## <a name="operator-equality"></a>ComPtr:: operator = =

Wskazuje, czy `ComPtr` dwa obiekty są równe.

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

*a*<br/>
Odwołanie do `ComPtr` obiektu.

*b*<br/>
Odwołanie do innego `ComPtr` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy plony operator `true` Jeśli obiekt *a* jest równy obiektowi *b*; w przeciwnym razie `false`.

Operatory drugi i trzeci uzyskanie `true` Jeśli obiekt *a* jest równa `nullptr`; w przeciwnym razie `false`.

## <a name="operator-inequality"></a>ComPtr:: operator! =

Wskazuje, czy `ComPtr` dwa obiekty nie są równe.

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

*a*<br/>
Odwołanie do `ComPtr` obiektu.

*b*<br/>
Odwołanie do innego `ComPtr` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy plony operator `true` Jeśli obiekt *a* nie jest równa obiektu *b*; w przeciwnym razie `false`.

Operatory drugi i trzeci uzyskanie `true` Jeśli obiekt *a* nie jest równa `nullptr`; w przeciwnym razie `false`.

## <a name="operator-microsoft-wrl-details-booltype"></a>ComPtr:: operator Microsoft:: WRL::D etails:: BoolType

Wskazuje, `ComPtr` czy zarządza okresem istnienia obiektu w interfejsie.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli interfejs jest skojarzony z tym `ComPtr`, adresem elementu członkowskiego danych [BoolStruct:: member](boolstruct-structure.md#member) ; w przeciwnym razie, `nullptr`.

## <a name="ptr"></a>ComPtr::ptr_

Zawiera wskaźnik do interfejsu, który jest skojarzony z i zarządzany przez ten `ComPtr`obiekt.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Uwagi

`ptr_`to wewnętrzny, chroniony element członkowski danych.

## <a name="releaseandgetaddressof"></a>ComPtr:: ReleaseAndGetAddressOf —

Zwalnia interfejs skojarzony z tym `ComPtr` , a następnie pobiera adres elementu członkowskiego danych [ptr_](#ptr) , który zawiera wskaźnik do wydanego interfejsu.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Adres elementu członkowskiego [](#ptr) `ComPtr`danych ptr_.

## <a name="reset"></a>ComPtr:: Reset

Zwalnia wszystkie odwołania dla wskaźnika do interfejsu, który jest skojarzony z tym `ComPtr`.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wydanych odwołań (jeśli istnieją).

## <a name="swap"></a>ComPtr:: swap

Wymienia interfejs zarządzany przez bieżącą `ComPtr` z interfejsem zarządzanym przez określony. `ComPtr`

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Parametry

*r*<br/>
A `ComPtr`.

