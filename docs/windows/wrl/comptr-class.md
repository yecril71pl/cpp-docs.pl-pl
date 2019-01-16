---
title: ComPtr — Klasa
ms.date: 10/01/2018
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
ms.openlocfilehash: da6d0761b60257bc4b0232123d179e9c04465844
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335010"
---
# <a name="comptr-class"></a>ComPtr — Klasa

Tworzy *inteligentny wskaźnik* typ, który reprezentuje interfejs określony przez parametr szablonu. `ComPtr` automatycznie przechowuje licznik odwołań dla podstawowego wskaźnika interfejsu i zwalnia interfejs gdy liczba odwołań osiąga zero.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Interfejs, `ComPtr` reprezentuje.

*U*<br/>
Klasa, do którego bieżący `ComPtr` jest zaprzyjaźniony. (Szablonu, który jest używany ten parametr jest chroniony).

## <a name="remarks"></a>Uwagi

`ComPtr<>` deklaruje typ, który reprezentuje podstawowego wskaźnika interfejsu. Użyj `ComPtr<>` zadeklarować zmienną, a następnie użyć operatora dostępu do elementu członkowskiego strzałkę (`->`) na dostęp do funkcji składowej interfejsu.

Aby uzyskać więcej informacji dotyczących inteligentnych wskaźników, zobacz podsekcję "Inteligentne wskaźniki COM" [praktyk kodowania COM](/windows/desktop/LearnWin32/com-coding-practices) w bibliotece MSDN.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa            | Opis
--------------- | ---------------------------------------------------------------
`InterfaceType` | Synonim dla typu określonego przez *T* parametru szablonu.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                             | Opis
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | Aktywuje nowe wystąpienie klasy `ComPtr` klasy. Przeciążenia zawierają konstruktory domyślne, kopiowanie, przenoszenie i konwersji.
[ComPtr::~ComPtr](#tilde-comptr) | Wyłącza wystąpienie `ComPtr`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                      | Opis
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr::As](#as)                                         | Zwraca `ComPtr` obiekt, który reprezentuje interfejs identyfikowane za pomocą parametru określonego szablonu.
[ComPtr::AsIID](#asiid)                                   | Zwraca `ComPtr` obiekt, który reprezentuje interfejs identyfikowane przez identyfikator określonego interfejsu.
[ComPtr::AsWeak](#asweak)                                 | Pobiera słabe odwołanie do bieżącego obiektu.
[ComPtr::Attach](#attach)                                 | To skojarzenie `ComPtr` z typu interfejsu, określonego przez bieżący parametrowi typu szablonu.
[ComPtr::CopyTo](#copyto)                                 | Kopiuje skojarzony z tym interfejs bieżącej lub określonej `ComPtr` wskaźnik określonym produktem wyjściowym.
[ComPtr::Detach](#detach)                                 | Powoduje to usunięcie `ComPtr` z interfejsu, który reprezentuje.
[ComPtr::Get](#get)                                       | Pobiera wskaźnik do interfejsu, który jest skojarzony z tym `ComPtr`.
[ComPtr::GetAddressOf](#getaddressof)                     | Pobiera adres [ptr_ — element](#ptr) element członkowski danych, który zawiera wskaźnik do interfejsu, reprezentowane przez to `ComPtr`.
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Zwalnia interfejs skojarzony z tym `ComPtr` i następnie pobiera adres [ptr_ — element](#ptr) element członkowski danych, który zawiera wskaźnik do interfejsu, który został wydany.
[ComPtr::Reset](#reset)                                   | Zwalnia wszystkie odwołania dla wskaźnika do interfejsu, który jest skojarzony z tym `ComPtr`.
[ComPtr::Swap](#swap)                                     | Wymienia interfejsu zarządzany przez bieżący `ComPtr` przy użyciu interfejsu, zarządzana przez określony `ComPtr`.

### <a name="protected-methods"></a>Metody chronione

Nazwa                                        | Opis
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | Zwiększa liczbę odwołań interfejsu skojarzony z tym `ComPtr`.
[ComPtr::InternalRelease](#internalrelease) | Wykonuje operację wydania COM w interfejsie skojarzony z tym `ComPtr`.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                                                           | Opis
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operator &](#operator-ampersand)                                                       | Pobiera adres bieżącej `ComPtr`.
[ComPtr::operator->](#operator-arrow)                                                          | Pobiera wskaźnik do typu określonego przez parametr bieżącego szablonu.
[ComPtr::operator=](#operator-assign)                                                          | Przypisuje wartość do bieżącego `ComPtr`.
[ComPtr::operator==](#operator-equality)                                                       | Wskazuje, czy dwa `ComPtr` obiekty są sobie równe.
[ComPtr::operator! =](#operator-inequality)                                                     | Wskazuje, czy dwa `ComPtr` obiekty nie są równe.
[ComPtr::operator Microsoft::WRL::Details::BoolType](#operator-microsoft-wrl-details-booltype) | Wskazuje, czy `ComPtr` Zarządzanie okresem istnienia interfejsu.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                 | Opis
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | Zawiera wskaźnik do interfejsu, który jest skojarzony z i zarządzanego przez to `ComPtr`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="tilde-comptr"></a>ComPtr::~ComPtr

Wyłącza wystąpienie `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>ComPtr::As

Zwraca `ComPtr` obiekt, który reprezentuje interfejs identyfikowane za pomocą parametru określonego szablonu.

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
Interfejs może być reprezentowana przez parametr *p*.

*p*<br/>
A `ComPtr` obiekt, który reprezentuje interfejs określony przez parametr *U*. Parametr *p* nie może odwoływać się do bieżącego `ComPtr` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy szablon jest formularz, który należy używać w kodzie. Drugi szablon jest wewnętrznych specjalizacji pomocnika, która obsługuje funkcje języka C++, takie jak [automatycznie](../../cpp/auto-cpp.md) słowem kluczowym dedukcji typu.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="asiid"></a>ComPtr::AsIID

Zwraca `ComPtr` obiekt, który reprezentuje interfejs identyfikowane przez identyfikator określonego interfejsu.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
Identyfikator interfejsu.

*p*<br/>
Jeśli obiekt ma interfejs, którego identyfikator jest równy *riid*, podwójnie pośredniego wskaźnika do interfejsu, określonego przez *riid* parametru; w przeciwnym razie wskaźnik do `IUnknown`.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="asweak"></a>ComPtr::AsWeak

Pobiera słabe odwołanie do bieżącego obiektu.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Parametry

*pWeakRef*<br/>
Gdy ta operacja zostanie ukończone, wskaźnik do obiektu słabe odwołanie.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="attach"></a>ComPtr::Attach

To skojarzenie `ComPtr` z typu interfejsu, określonego przez bieżący parametrowi typu szablonu.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parametry

*other*<br/>
Typ interfejsu.

## <a name="comptr"></a>ComPtr::ComPtr

Aktywuje nowe wystąpienie klasy `ComPtr` klasy. Przeciążenia zawierają konstruktory domyślne, kopiowanie, przenoszenie i konwersji.

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
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
```

### <a name="parameters"></a>Parametry

*U*<br/>
Typ *innych* parametru.

*other*<br/>
Obiekt typu *U*.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor jest konstruktor domyślny, która niejawnie tworzy pustego obiektu. Drugi Konstruktor Określa [__nullptr](../nullptr-cpp-component-extensions.md), co powoduje jawne utworzenie pustego obiektu.

Trzeci Konstruktor tworzy obiekt w obiekcie określonym przez wskaźnik.

Konstruktory czwarty i piąty są konstruktorów kopiujących. Piąty Konstruktor kopiuje obiekt, jeśli jest konwertowany na typ bieżącego.

Konstruktory szóstego lub siódmego są konstruktorów przenoszenia. Siódmego Konstruktor przenosi obiekt, jeśli jest konwertowany na typ bieżącego.

## <a name="copyto"></a>ComPtr::CopyTo

Kopiuje skojarzony z tym interfejs bieżącej lub określonej `ComPtr` określony wskaźnik.

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
Gdy ta operacja zostanie ukończone, wskaźnik do żądanego interfejsu.

*Parametr riid*<br/>
Identyfikator interfejsu.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje, dlaczego niejawny `QueryInterface` operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja zwraca kopię wskaźnika do interfejsu, który został skojarzony z tym `ComPtr`. Ta funkcja zawsze zwraca wartość S_OK.

Druga funkcja wykonuje `QueryInterface` operacji w interfejsie skojarzony z tym `ComPtr` dla interfejsu, określonego przez *riid* parametru.

Trzecia funkcja wykonuje `QueryInterface` operacji w interfejsie skojarzony z tym `ComPtr` dla podstawowego interfejsu *U* parametru.

## <a name="detach"></a>ComPtr::Detach

Powoduje to usunięcie `ComPtr` obiektu z interfejsu, który reprezentuje.

```cpp
T* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który został przedstawiony przez ten `ComPtr` obiektu.

## <a name="get"></a>ComPtr::Get

Pobiera wskaźnik do interfejsu, który jest skojarzony z tym `ComPtr`.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który jest skojarzony z tym `ComPtr`.

## <a name="getaddressof"></a>ComPtr::GetAddressOf

Pobiera adres [ptr_ — element](#ptr) element członkowski danych, który zawiera wskaźnik do interfejsu, reprezentowane przez to `ComPtr`.

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Adres zmiennej.

## <a name="internaladdref"></a>ComPtr::InternalAddRef

Zwiększa liczbę odwołań interfejsu skojarzony z tym `ComPtr`.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Uwagi

Ta metoda jest chroniona.

## <a name="internalrelease"></a>ComPtr::InternalRelease

Wykonuje operację wydania COM w interfejsie skojarzony z tym `ComPtr`.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest chroniona.

## <a name="operator-ampersand"></a>ComPtr::operator&amp;

Zwalnia interfejs skojarzony z tym `ComPtr` obiektu, a następnie pobiera adres `ComPtr` obiektu.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Wartość zwracana

Słabe odwołanie do bieżącego `ComPtr`.

### <a name="remarks"></a>Uwagi

Ta metoda różni się od [ComPtr::GetAddressOf](#getaddressof) w tym, że ta metoda wydaje odniesienie do wskaźnika interfejsu. Użyj `ComPtr::GetAddressOf` po adresu wskaźnik interfejsu, ale nie chcesz zwolnić interfejsu.

## <a name="operator-arrow"></a>ComPtr::operator-&gt;

Pobiera wskaźnik do typu określonego przez parametr bieżącego szablonu.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do typu określonego przez nazwę typu bieżącego szablonu.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika usuwa niepotrzebne obciążenie spowodowane użyciem STDMETHOD — makro. Ta funkcja sprawia, że `IUnknown` typy `private` zamiast `virtual`.

## <a name="operator-assign"></a>ComPtr::operator =

Przypisuje wartość do bieżącego `ComPtr`.

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
Wskaźnik, odwołanie lub odwołanie rvalue typu lub innej `ComPtr`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego `ComPtr`.

### <a name="remarks"></a>Uwagi

Pierwsza wersja tego operatora przypisuje wartość pustą do bieżącego `ComPtr`.

W drugiej wersji, jeśli przypisanie wskaźnika interfejsu nie jest taka sama jak bieżący `ComPtr` wskaźnik interfejsu, drugi wskaźnik interfejsu jest przypisany do bieżącego `ComPtr`.

W trzeciej wersji przypisywanie wskaźnika interfejsu jest przypisany do bieżącego `ComPtr`.

W czwartym wersji, jeśli wskaźnik interfejsu, przypisywanie wartości nie jest taka sama jak bieżący `ComPtr` wskaźnik interfejsu, drugi wskaźnik interfejsu jest przypisany do bieżącego `ComPtr`.

Piąta wersja jest operator kopiowania; Odwołanie do `ComPtr` jest przypisany do bieżącego `ComPtr`.

Szósty wersji jest operator kopii, który używa semantyki; przenoszenia odwołania rvalue do `ComPtr` Jeśli dowolnego typu jest statycznego, cast i przypisywany do bieżącego `ComPtr`.

Wersja siódmego jest operator kopii, który używa semantyki; przenoszenia odwołania rvalue do `ComPtr` typu *U* statyczne następnie rzutowania i ma przypisaną do bieżącego `ComPtr`.

## <a name="operator-equality"></a>ComPtr::operator==

Wskazuje, czy dwa `ComPtr` obiekty są sobie równe.

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

## <a name="operator-inequality"></a>ComPtr::operator! =

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

*a*<br/>
Odwołanie do `ComPtr` obiektu.

*b*<br/>
Odwołanie do innego `ComPtr` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy plony operator `true` Jeśli obiekt *a* nie jest równa obiektu *b*; w przeciwnym razie `false`.

Operatory drugi i trzeci uzyskanie `true` Jeśli obiekt *a* nie jest równa `nullptr`; w przeciwnym razie `false`.

## <a name="operator-microsoft-wrl-details-booltype"></a>ComPtr::operator Microsoft::WRL::Details::BoolType

Wskazuje, czy `ComPtr` Zarządzanie okresem istnienia interfejsu.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli interfejs jest skojarzony z tym `ComPtr`, adres [BoolStruct::Member](boolstruct-structure.md#member) element członkowski danych; w przeciwnym razie `nullptr`.

## <a name="ptr"></a>ComPtr::ptr_

Zawiera wskaźnik do interfejsu, który jest skojarzony z i zarządzanego przez to `ComPtr`.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Uwagi

`ptr_` jest elementem członkowskim wewnętrznego, chronionych danych.

## <a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

Zwalnia interfejs skojarzony z tym `ComPtr` i następnie pobiera adres [ptr_ — element](#ptr) element członkowski danych, który zawiera wskaźnik do interfejsu, który został wydany.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Adres [ptr_ — element](#ptr) to element członkowski danych `ComPtr`.

## <a name="reset"></a>ComPtr::Reset

Zwalnia wszystkie odwołania dla wskaźnika do interfejsu, który jest skojarzony z tym `ComPtr`.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Wartość zwracana

Liczba odwołań do wydania, jeśli istnieje.

## <a name="swap"></a>ComPtr::Swap

Wymienia interfejsu zarządzany przez bieżący `ComPtr` przy użyciu interfejsu, zarządzana przez określony `ComPtr`.

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

