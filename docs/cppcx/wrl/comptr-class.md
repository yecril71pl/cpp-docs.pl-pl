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
ms.openlocfilehash: 89c09ede972f5bdd5da1dde810cad31733bdf338
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372637"
---
# <a name="comptr-class"></a>ComPtr — Klasa

Tworzy typ *inteligentnego wskaźnika* reprezentujący interfejs określony przez parametr szablonu. `ComPtr`automatycznie utrzymuje liczbę odwołań dla wskaźnika interfejsu źródłowego i zwalnia interfejs, gdy liczba odwołań wynosi zero.

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
Klasa, do której `ComPtr` prąd jest przyjacielem. (Szablon, który używa tego parametru jest chroniony.)

## <a name="remarks"></a>Uwagi

`ComPtr<>`deklaruje typ, który reprezentuje wskaźnik interfejsu źródłowego. Służy `ComPtr<>` do deklarowania zmiennej, a następnie`->`użyj operatora dostępu do elementu członkowskiego strzałki ( ) w celu uzyskania dostępu do funkcji elementu członkowskiego interfejsu.

Aby uzyskać więcej informacji na temat inteligentnych wskaźników, zobacz podsekcję "Inteligentne wskaźniki COM" tematu [Praktyki kodowania COM](/windows/win32/LearnWin32/com-coding-practices) w bibliotece MSDN.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa            | Opis
--------------- | ---------------------------------------------------------------
`InterfaceType` | Synonim dla typu określonego przez parametr szablonu *T.*

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                             | Opis
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | Intializes nowe wystąpienie `ComPtr` klasy. Przeciążenia zapewniają domyślne, kopiowanie, przenoszenie i konstruktory konwersji.
[ComPtr::~ComPtr](#tilde-comptr) | Deinitializes wystąpienie `ComPtr`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                      | Opis
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr::W](#as)                                         | Zwraca `ComPtr` obiekt reprezentujący interfejs identyfikowany przez określony parametr szablonu.
[ComPtr::AsIID](#asiid)                                   | Zwraca `ComPtr` obiekt reprezentujący interfejs identyfikowany przez określony identyfikator interfejsu.
[ComPtr::AsWeak](#asweak)                                 | Pobiera słabe odwołanie do bieżącego obiektu.
[ComPtr::Dołącz](#attach)                                 | Kojarzy `ComPtr` to z typem interfejsu określonym przez bieżący parametr typu szablonu.
[ComPtr::CopyTo](#copyto)                                 | Kopiuje bieżący lub określony `ComPtr` interfejs skojarzony z tym do określonego wskaźnika wyjściowego.
[ComPtr::Detach](#detach)                                 | Disassociates `ComPtr` to z interfejsu, który reprezentuje.
[ComPtr::Pobierz](#get)                                       | Pobiera wskaźnik do interfejsu, który jest `ComPtr`skojarzony z tym .
[ComPtr::GetAddressOf](#getaddressof)                     | Pobiera adres [elementu](#ptr) członkowskiego ptr_ danych, który zawiera wskaźnik do interfejsu `ComPtr`reprezentowanego przez ten plik .
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Zwalnia interfejs skojarzony `ComPtr` z tym, a następnie pobiera adres [ptr_](#ptr) elementu członkowskiego danych, który zawiera wskaźnik do interfejsu, który został zwolniony.
[ComPtr::Reset](#reset)                                   | Zwalnia wszystkie odwołania do wskaźnika do interfejsu, `ComPtr`który jest skojarzony z tym .
[ComPtr::Zamiana](#swap)                                     | Wymienia interfejs zarządzany przez `ComPtr` prąd z interfejsem `ComPtr`zarządzanym przez określony plik .

### <a name="protected-methods"></a>Metody chronione

Nazwa                                        | Opis
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | Zwiększa liczbę odwołań interfejsu skojarzonego z `ComPtr`tym programem .
[ComPtr::InternalRelease](#internalrelease) | Wykonuje operację wydania COM na interfejsie `ComPtr`skojarzonym z tym .

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                                                           | Opis
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operator&](#operator-ampersand)                                                       | Pobiera adres bieżącego `ComPtr`.
[ComPtr::operator->](#operator-arrow)                                                          | Pobiera wskaźnik do typu określonego przez bieżący parametr szablonu.
[ComPtr::operator=](#operator-assign)                                                          | Przypisuje wartość do bieżącego `ComPtr`.
[ComPtr::operator==](#operator-equality)                                                       | Wskazuje, czy `ComPtr` dwa obiekty są równe.
[ComPtr::operator!=](#operator-inequality)                                                     | Wskazuje, czy `ComPtr` dwa obiekty nie są równe.
[ComPtr::operator Microsoft::WRL::Details::BoolType](#operator-microsoft-wrl-details-booltype) | Wskazuje, czy a `ComPtr` zarządza okresem istnienia obiektu interfejsu.

### <a name="protected-data-members"></a>Członkowie chronionych danych

Nazwa                 | Opis
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | Zawiera wskaźnik do interfejsu, który jest skojarzony `ComPtr`z i zarządzane przez ten program .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Obszar nazw:** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>ComPtr::~ComPtr

Deinitializes wystąpienie `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>ComPtr::W

Zwraca `ComPtr` obiekt reprezentujący interfejs identyfikowany przez określony parametr szablonu.

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

*P*<br/>
Obiekt `ComPtr` reprezentujący interfejs określony przez parametr *U*. Parametr *p* nie może `ComPtr` odnosić się do bieżącego obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy szablon jest formularz, który należy użyć w kodzie. Drugi szablon jest wewnętrzna, pomocnicza specjalizacja, która [auto](../../cpp/auto-cpp.md) obsługuje funkcje języka C++, takie jak słowo kluczowe auto-dedukcji typu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

## <a name="comptrasiid"></a><a name="asiid"></a>ComPtr::AsIID

Zwraca `ComPtr` obiekt reprezentujący interfejs identyfikowany przez określony identyfikator interfejsu.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Identyfikator interfejsu.

*P*<br/>
Jeśli obiekt ma interfejs, którego identyfikator jest *równy riid*, podwójnie pośredni wskaźnik do interfejsu określonego przez *riid* parametru; w przeciwnym razie `IUnknown`wskaźnik do .

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

## <a name="comptrasweak"></a><a name="asweak"></a>ComPtr::AsWeak

Pobiera słabe odwołanie do bieżącego obiektu.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Parametry

*pWeakRef (Odnośnik od łowy)*<br/>
Po zakończeniu tej operacji wskaźnik do obiektu słabe odniesienia.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

## <a name="comptrattach"></a><a name="attach"></a>ComPtr::Dołącz

Kojarzy `ComPtr` to z typem interfejsu określonym przez bieżący parametr typu szablonu.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Typ interfejsu.

## <a name="comptrcomptr"></a><a name="comptr"></a>ComPtr::ComPtr

Intializes nowe wystąpienie `ComPtr` klasy. Przeciążenia zapewniają domyślne, kopiowanie, przenoszenie i konstruktory konwersji.

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
Typ *innego* parametru.

*Innych*<br/>
Obiekt typu *U*.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor jest domyślnym konstruktorem, który implictly tworzy pusty obiekt. Drugi konstruktor określa [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), który jawnie tworzy pusty obiekt.

Trzeci konstruktor tworzy obiekt z obiektu określonego przez wskaźnik. ComPtr jest teraz właścicielem pamięci wskazał do i utrzymuje liczbę odwołań do niego.

Konstruktory czwarty i piąty są konstruktory kopii. Piąty konstruktor kopiuje obiekt, jeśli jest konwertowany na bieżący typ.

Konstruktory szóstego i siódmego są konstruktorami ruchu. Siódmy konstruktor przenosi obiekt, jeśli jest konwertowany na bieżący typ.

## <a name="comptrcopyto"></a><a name="copyto"></a>ComPtr::CopyTo

Kopiuje bieżący lub określony `ComPtr` interfejs skojarzony z tym do określonego wskaźnika.

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

*Ptr*<br/>
Po zakończeniu tej operacji wskaźnik do żądanego interfejsu.

*Riid*<br/>
Identyfikator interfejsu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który `QueryInterface` wskazuje, dlaczego operacja niejawna nie powiodło się.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja zwraca kopię wskaźnika do interfejsu skojarzonego z tym programem `ComPtr`. Ta funkcja zawsze zwraca S_OK.

Druga funkcja wykonuje `QueryInterface` operację na interfejsie skojarzonym z tym `ComPtr` dla interfejsu określonego przez parametr *riid.*

Trzecia funkcja wykonuje `QueryInterface` operację na interfejsie skojarzonym z tym `ComPtr` dla interfejsu źródłowego parametru *U.*

## <a name="comptrdetach"></a><a name="detach"></a>ComPtr::Detach

Disassociates `ComPtr` tego obiektu z interfejsu, który reprezentuje.

```cpp
T* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który był `ComPtr` reprezentowany przez ten obiekt.

## <a name="comptrget"></a><a name="get"></a>ComPtr::Pobierz

Pobiera wskaźnik do interfejsu, który jest `ComPtr`skojarzony z tym .

```cpp
T* Get() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który jest `ComPtr`skojarzony z tym .

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>ComPtr::GetAddressOf

Pobiera adres [elementu](#ptr) członkowskiego ptr_ danych, który zawiera wskaźnik do interfejsu `ComPtr`reprezentowanego przez ten plik .

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Adres zmiennej.

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>ComPtr::InternalAddRef

Zwiększa liczbę odwołań interfejsu skojarzonego z `ComPtr`tym programem .

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Uwagi

Ta metoda jest chroniona.

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>ComPtr::InternalRelease

Wykonuje operację wydania COM na interfejsie `ComPtr`skojarzonym z tym .

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest chroniona.

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>ComPtr::operator&amp;

Zwalnia interfejs skojarzony `ComPtr` z tym obiektem, a `ComPtr` następnie pobiera adres obiektu.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Wartość zwracana

Słabe odniesienie do `ComPtr`bieżącego .

### <a name="remarks"></a>Uwagi

Ta metoda różni się od [ComPtr::GetAddressOf](#getaddressof) w tym tej metody zwalnia odwołanie do wskaźnika interfejsu. Użyj, `ComPtr::GetAddressOf` gdy potrzebujesz adresu wskaźnika interfejsu, ale nie chcesz zwolnić tego interfejsu.

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>ComPtr::operator-&gt;

Pobiera wskaźnik do typu określonego przez bieżący parametr szablonu.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do typu określonego przez bieżącą nazwę typu szablonu.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika usuwa niepotrzebne obciążenie spowodowane użyciem makra STDMETHOD. Ta funkcja `IUnknown` `private` sprawia, `virtual`że typy zamiast .

## <a name="comptroperator"></a><a name="operator-assign"></a>ComPtr::operator=

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

*Innych*<br/>
Odwołanie do wskaźnika, odwołania lub wartości r `ComPtr`do typu lub innego .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego `ComPtr`.

### <a name="remarks"></a>Uwagi

Pierwsza wersja tego operatora przypisuje pustą wartość `ComPtr`do bieżącego .

W drugiej wersji, jeśli przypisujący wskaźnik interfejsu nie `ComPtr` jest taki sam jak bieżący wskaźnik `ComPtr`interfejsu, drugi wskaźnik interfejsu jest przypisany do bieżącego .

W trzeciej wersji wskaźnik interfejsu przypisującego jest `ComPtr`przypisany do bieżącego pliku .

W czwartej wersji, jeśli wskaźnik interfejsu wartości przypisywania nie `ComPtr` jest taki sam jak bieżący wskaźnik `ComPtr`interfejsu, drugi wskaźnik interfejsu jest przypisany do bieżącego .

Piąta wersja jest operatorem kopiowania; odwołanie do `ComPtr` a jest przypisane `ComPtr`do bieżącego .

Szósta wersja jest operatorem kopiowania, który używa semantyki przenoszenia; odwołanie rvalue `ComPtr` do, jeśli dowolny typ jest rzutem statycznym, a następnie przypisany do bieżącego `ComPtr`.

Siódma wersja jest operatorem kopiowania, który używa semantyki przenoszenia; odwołanie rvalue do `ComPtr` typu *U* jest rzutem statycznym i `ComPtr`przypisane do bieżącego .

## <a name="comptroperator"></a><a name="operator-equality"></a>ComPtr::operator==

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

*A*<br/>
Odwołanie do `ComPtr` obiektu.

*B*<br/>
Odwołanie do `ComPtr` innego obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator daje, `true` jeśli obiekt *a* jest równy obiektowi *b*; w `false`przeciwnym razie , .

Drugi i trzeci `true` operator dają, jeśli `nullptr`obiekt *a* jest równy ; w `false`przeciwnym razie , .

## <a name="comptroperator"></a><a name="operator-inequality"></a>ComPtr::operator!=

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

*A*<br/>
Odwołanie do `ComPtr` obiektu.

*B*<br/>
Odwołanie do `ComPtr` innego obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator daje, `true` jeśli obiekt *a* nie jest równy obiektowi *b*; w `false`przeciwnym razie , .

Drugi i trzeci `true` operator dają, jeśli `nullptr`obiekt *a* nie jest równy ; w `false`przeciwnym razie , .

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>ComPtr::operator Microsoft::WRL::Details::BoolType

Wskazuje, czy a `ComPtr` zarządza okresem istnienia obiektu interfejsu.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli interfejs jest skojarzony `ComPtr`z tym , adres [BoolStruct::Element](boolstruct-structure.md#member) członkowski danych; w `nullptr`przeciwnym razie , .

## <a name="comptrptr_"></a><a name="ptr"></a>ComPtr::ptr_

Zawiera wskaźnik do interfejsu, który jest skojarzony `ComPtr`z i zarządzane przez ten program .

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Uwagi

`ptr_`jest wewnętrznym, chronionym elementem członkowskim danych.

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

Zwalnia interfejs skojarzony `ComPtr` z tym, a następnie pobiera adres [ptr_](#ptr) elementu członkowskiego danych, który zawiera wskaźnik do interfejsu, który został zwolniony.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Adres [ptr_](#ptr) członka danych tego `ComPtr`.

## <a name="comptrreset"></a><a name="reset"></a>ComPtr::Reset

Zwalnia wszystkie odwołania do wskaźnika do interfejsu, `ComPtr`który jest skojarzony z tym .

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Wartość zwracana

Liczba odwołań zwolnionych, jeśli istnieje.

## <a name="comptrswap"></a><a name="swap"></a>ComPtr::Zamiana

Wymienia interfejs zarządzany przez `ComPtr` prąd z interfejsem `ComPtr`zarządzanym przez określony plik .

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Parametry

*R*<br/>
Klasa `ComPtr`.
