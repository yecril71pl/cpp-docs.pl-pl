---
title: WeakRef — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
- client/Microsoft::WRL::WeakRef::~WeakRef
- client/Microsoft::WRL::WeakRef::As
- client/Microsoft::WRL::WeakRef::AsIID
- client/Microsoft::WRL::WeakRef::CopyTo
- client/Microsoft::WRL::WeakRef::operator&
- client/Microsoft::WRL::WeakRef::WeakRef
helpviewer_keywords:
- Microsoft::WRL::WeakRef class
- Microsoft::WRL::WeakRef::~WeakRef, destructor
- Microsoft::WRL::WeakRef::As method
- Microsoft::WRL::WeakRef::AsIID method
- Microsoft::WRL::WeakRef::CopyTo method
- Microsoft::WRL::WeakRef::operator& operator
- Microsoft::WRL::WeakRef::WeakRef, constructor
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
ms.openlocfilehash: 9616fcffac0b92d5ac6d96cfe5f4119f3a3b180f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787430"
---
# <a name="weakref-class"></a>WeakRef — Klasa

Reprezentuje *słabe odwołanie* mogą służyć tylko Windows środowisko wykonawcze, nie Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.

## <a name="syntax"></a>Składnia

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[WeakRef::WeakRef, konstruktor](#weakref)|Inicjuje nowe wystąpienie klasy `WeakRef` klasy.|
|[WeakRef::~WeakRef, destruktor](#tilde-weakref)|Deinicjuje bieżące wystąpienie `WeakRef` klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[WeakRef::As, metoda](#as)|Ustawia określony `ComPtr` parametru wskaźnika do reprezentowania określonego interfejsu.|
|[WeakRef::AsIID, metoda](#asiid)|Ustawia określony `ComPtr` parametru wskaźnika do reprezentowania identyfikatora określonego interfejsu.|
|[WeakRef::CopyTo, metoda](#copyto)|Przypisuje wskaźnik interfejsu, jeśli to możliwe, do zmiennej wskaźnika określonej.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator WeakRef::operator&](#operator-ampersand-operator)|Zwraca `ComPtrRef` obiekt, który reprezentuje bieżący `WeakRef` obiektu.|

## <a name="remarks"></a>Uwagi

A `WeakRef` obiekt zachowuje *silne odwołanie*, który jest skojarzony z obiektem i może być prawidłowy lub nieprawidłowy. Wywołaj `As()` lub `AsIID()` metodę, aby uzyskać silne odwołanie. Gdy silne odwołanie są poprawne, dostęp skojarzonego obiektu. Jeśli silne odwołanie jest nieprawidłowe (`nullptr`), skojarzonego obiektu jest niedostępny.

A `WeakRef` obiekt jest zwykle używana do reprezentowania obiekt, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład, utworzyć `WeakRef` obiektu z odwołaniem do obiektu pliku. Gdy plik jest otwarty, silne odwołanie jest prawidłowy. Ale jeśli ten plik będzie zamknięty, silne odwołanie staje się nieprawidłowy.

Należy pamiętać, że zmiana zachowania [jako](#as), [asiid —](#asiid) i [CopyTo](#copyto) metody w zestawie SDK systemu Windows 10. Wcześniej, po wywołaniu dowolnej z tych metod, możesz sprawdzić `WeakRef` dla `nullptr` ustalenie, jeśli silne odwołanie pomyślnie uzyskano, zgodnie z poniższym kodem:

```cpp
WeakRef wr;
strongComptrRef.AsWeak(&wr);

// Now suppose that the object strongComPtrRef points to no longer exists
// and the following code tries to get a strong ref from the weak ref:
ComPtr<ISomeInterface> strongRef;
HRESULT hr = wr.As(&strongRef);

// This check won't work with the Windows 10 SDK version of the library.
// Check the input pointer instead.
if(wr == nullptr)
{
    wprintf(L"Couldn’t get strong ref!");
}
```

Powyższy kod nie działa, korzystając z zestawu Windows 10 SDK (lub nowszego). Zamiast tego należy sprawdzić wskaźnika, która została przekazana dla `nullptr`.

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtr`

`WeakRef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="tilde-weakref"></a>WeakRef:: ~ WeakRef, destruktor

Deinicjuje bieżące wystąpienie `WeakRef` klasy.

```cpp
~WeakRef();
```

## <a name="as"></a>WeakRef::As, metoda

Ustawia określony `ComPtr` parametru wskaźnika do reprezentowania określonego interfejsu.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>Parametry

*U*<br/>
Identyfikator interfejsu.

*ptr*<br/>
Po zakończeniu tej operacji, obiekt, który reprezentuje parametr *U*.

### <a name="return-value"></a>Wartość zwracana

- S_OK, jeśli operacja się powiedzie; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę operacja nie powiodła się, a *ptr* ustawiono `nullptr`.

- S_OK, jeśli operacja zakończy się powodzeniem, ale bieżący `WeakRef` obiekt został zwolniony. Parametr *ptr* ustawiono `nullptr`.

- S_OK, jeśli operacja zakończy się powodzeniem, ale bieżący `WeakRef` obiektu nie jest tworzony na podstawie parametru *U*. Parametr *ptr* ustawiono `nullptr`.

### <a name="remarks"></a>Uwagi

Błąd jest emitowane, jeśli parametr *U* jest `IWeakReference`, lub nie jest tworzony na podstawie `IInspectable`.

Pierwszy szablon jest formularz, który należy używać w kodzie. Drugi szablon jest wewnętrznych specjalizacji pomocnika, która obsługuje funkcje języka C++, takie jak [automatycznie](../../cpp/auto-cpp.md) słowem kluczowym dedukcji typu.

Począwszy od zestawu Windows 10 SDK, ta metoda nie ustawia `WeakRef` wystąpienia do `nullptr` Jeśli nie można uzyskać słabe odwołanie, więc należy unikać sprawdzanie błędów kodu, który sprawdza `WeakRef` dla `nullptr`. Zamiast tego należy sprawdzić *ptr* dla `nullptr`.

## <a name="asiid"></a>WeakRef::AsIID, metoda

Ustawia określony `ComPtr` parametru wskaźnika do reprezentowania identyfikatora określonego interfejsu.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
Identyfikator interfejsu.

*ptr*<br/>
Po zakończeniu tej operacji, obiekt, który reprezentuje parametr *riid*.

### <a name="return-value"></a>Wartość zwracana

- S_OK, jeśli operacja się powiedzie; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę operacja nie powiodła się, a *ptr* ustawiono `nullptr`.

- S_OK, jeśli operacja zakończy się powodzeniem, ale bieżący `WeakRef` obiekt został zwolniony. Parametr *ptr* ustawiono `nullptr`.

- S_OK, jeśli operacja zakończy się powodzeniem, ale bieżący `WeakRef` obiektu nie jest tworzony na podstawie parametru *riid*. Parametr *ptr* ustawiono `nullptr`. (Aby uzyskać więcej informacji, zobacz Uwagi).

### <a name="remarks"></a>Uwagi

Błąd jest emitowane, jeśli parametr *riid* nie pochodzi od `IInspectable`. Ten błąd zastępuje wartość zwracaną.

Pierwszy szablon jest formularz, który należy używać w kodzie. Drugi (nie pokazane tutaj, ale zadeklarowana w pliku nagłówkowym) jest wewnętrznych specjalizacji pomocnika, która obsługuje funkcje języka C++, takie jak [automatycznie](../../cpp/auto-cpp.md) słowem kluczowym dedukcji typu.

Począwszy od zestawu Windows 10 SDK, ta metoda nie ustawia `WeakRef` wystąpienia do `nullptr` Jeśli nie można uzyskać słabe odwołanie, więc należy unikać sprawdzanie błędów kodu, który sprawdza `WeakRef` dla `nullptr`. Zamiast tego należy sprawdzić *ptr* dla `nullptr`.

## <a name="copyto"></a>WeakRef::CopyTo, metoda

Przypisuje wskaźnik interfejsu, jeśli to możliwe, do zmiennej wskaźnika określonej.

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>Parametry

*U*<br/>
Wskaźnik `IInspectable` interfejsu. Błąd jest emitowane, jeśli *U* nie pochodzi od `IInspectable`.

*Parametr riid*<br/>
Identyfikator interfejsu. Błąd jest emitowane, jeśli *riid* nie pochodzi od `IWeakReference`.

*ptr*<br/>
Podwójnie pośredniego wskaźnika do `IInspectable` lub `IWeakReference`.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd. Aby uzyskać więcej informacji, zobacz **uwagi**.

### <a name="remarks"></a>Uwagi

Zwracana wartość S_OK oznacza, że ta operacja zakończyło się pomyślnie, ale nie wskazuje, czy słabe odwołanie została rozpoznana jako silne odwołanie. Jeśli zwracana jest S_OK, przetestować ten parametr *p* jest silne odwołanie, czyli parametr *p* nie jest równa `nullptr`.

Począwszy od zestawu Windows 10 SDK, ta metoda nie ustawia `WeakRef` wystąpienia do `nullptr` Jeśli nie można uzyskać słabe odwołanie, więc należy unikać błąd podczas sprawdzania kodu, który sprawdza `WeakRef` dla `nullptr`. Zamiast tego należy sprawdzić *ptr* dla `nullptr`.

## <a name="operator-ampersand-operator"></a>WeakRef::operator&amp; — Operator

Zwraca `ComPtrRef` obiekt, który reprezentuje bieżący `WeakRef` obiektu.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Wartość zwracana

A `ComPtrRef` obiekt, który reprezentuje bieżący `WeakRef` obiektu.

### <a name="remarks"></a>Uwagi

Jest to wewnętrzny pomocnika operatora, który nie jest przeznaczona do użycia w kodzie.

## <a name="weakref"></a>WeakRef::WeakRef, Konstruktor

Inicjuje nowe wystąpienie klasy `WeakRef` klasy.

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik, odwołanie lub odwołanie rvalue do istniejącego obiektu, który inicjuje bieżące `WeakRef` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje pustą `WeakRef` obiektu. Drugi Konstruktor inicjuje `WeakRef` obiektu ze wskaźnika do `IWeakReference` interfejsu. Trzeci Konstruktor inicjuje `WeakRef` obiektu z odwołaniem do `ComPtr<IWeakReference>` obiektu. Czwarty i piąty Konstruktor inicjuje `WeakRef` obiektu z innego `WeakRef` obiektu.
