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
ms.openlocfilehash: 715a823784aaa75f9abe349ef0a7ddc9e5d607d1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218354"
---
# <a name="weakref-class"></a>WeakRef — Klasa

Reprezentuje *słabe odwołanie* , które może być używane tylko przez środowisko wykonawcze systemu Windows, a nie klasyczny com. Słabe odwołanie reprezentuje obiekt, który może lub nie jest dostępny.

## <a name="syntax"></a>Składnia

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[WeakRef::WeakRef, konstruktor](#weakref)|Inicjuje nowe wystąpienie klasy `WeakRef`.|
|[WeakRef::~WeakRef, destruktor](#tilde-weakref)|Deinicjalizuje bieżące wystąpienie `WeakRef` klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[WeakRef::As, metoda](#as)|Ustawia określony `ComPtr` parametr wskaźnika reprezentujący określony interfejs.|
|[WeakRef::AsIID, metoda](#asiid)|Ustawia określony `ComPtr` parametr wskaźnika reprezentujący określony identyfikator interfejsu.|
|[WeakRef::CopyTo, metoda](#copyto)|Przypisuje wskaźnik do interfejsu, jeśli jest dostępny, do określonej zmiennej wskaźnika.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator WeakRef::operator&](#operator-ampersand-operator)|Zwraca `ComPtrRef` obiekt, który reprezentuje bieżący `WeakRef` obiekt.|

## <a name="remarks"></a>Uwagi

`WeakRef`Obiekt zachowuje *silną referencję*, która jest skojarzona z obiektem i może być prawidłowa lub nieprawidłowa. Wywołaj `As()` metodę lub, `AsIID()` Aby uzyskać silne odwołanie. Gdy silne odwołanie jest prawidłowe, może uzyskać dostęp do skojarzonego obiektu. Gdy silne odwołanie jest nieprawidłowe ( **`nullptr`** ), skojarzony obiekt jest niedostępny.

`WeakRef`Obiekt jest zazwyczaj używany do reprezentowania obiektu, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład konstruowanie `WeakRef` obiektu z odwołania do obiektu pliku. Gdy plik jest otwarty, silne odwołanie jest prawidłowe. Ale jeśli plik jest zamknięty, silne odwołanie jest nieprawidłowe.

Należy zauważyć, że istnieje zmiana zachowania w metodach [as](#as), [AsIID —](#asiid) i [CopyTo](#copyto) w zestawie SDK systemu Windows 10. Wcześniej, po wywołaniu dowolnej z tych metod, można sprawdzić, `WeakRef` **`nullptr`** czy silna dokumentacja została pomyślnie uzyskana, jak w poniższym kodzie:

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

Powyższy kod nie działa w przypadku korzystania z zestawu Windows 10 SDK (lub nowszego). Zamiast tego Sprawdź wskaźnik, który został przesłany dla **`nullptr`** .

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

**Nagłówek:** Client. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a>WeakRef:: ~ WeakRef, destruktor

Deinicjalizuje bieżące wystąpienie `WeakRef` klasy.

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a>WeakRef:: as — Metoda

Ustawia określony `ComPtr` parametr wskaźnika reprezentujący określony interfejs.

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
Po zakończeniu tej operacji obiekt, który reprezentuje parametr *U*.

### <a name="return-value"></a>Wartość zwracana

- S_OK w przypadku pomyślnego wykonania tej operacji; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę niepowodzenia operacji, a *PTR* jest ustawiona na **`nullptr`** .

- S_OK, jeśli ta operacja zakończy się pomyślnie, ale bieżący `WeakRef` obiekt został już wystawiony. Parametr *PTR* ma ustawioną wartość **`nullptr`** .

- S_OK, jeśli ta operacja zakończy się pomyślnie, ale bieżący `WeakRef` obiekt nie pochodzi od parametru *U*. Parametr *PTR* ma ustawioną wartość **`nullptr`** .

### <a name="remarks"></a>Uwagi

Błąd jest emitowany, jeśli parametr *U* jest `IWeakReference` lub nie pochodzi od `IInspectable` .

Pierwszy szablon jest formularzem, którego należy użyć w kodzie. Drugi szablon jest wewnętrzną specjalizacją pomocnika, która obsługuje funkcje języka [C++, takie](../../cpp/auto-cpp.md) jak słowo kluczowe potrącenie typu autoodejmowanie.

Począwszy od zestawu SDK systemu Windows 10, ta metoda nie ustawia `WeakRef` wystąpienia na Jeśli nie można **`nullptr`** uzyskać słabej referencji, dlatego należy unikać sprawdzania błędów kodu, który sprawdza, czy `WeakRef` **`nullptr`** . Zamiast tego zaznacz *ptr* pole PTR **`nullptr`** .

## <a name="weakrefasiid-method"></a><a name="asiid"></a>WeakRef:: AsIID —, Metoda

Ustawia określony `ComPtr` parametr wskaźnika reprezentujący określony identyfikator interfejsu.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identyfikator interfejsu.

*ptr*<br/>
Po zakończeniu tej operacji obiekt, który reprezentuje parametr *riid*.

### <a name="return-value"></a>Wartość zwracana

- S_OK w przypadku pomyślnego wykonania tej operacji; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę niepowodzenia operacji, a *PTR* jest ustawiona na **`nullptr`** .

- S_OK, jeśli ta operacja zakończy się pomyślnie, ale bieżący `WeakRef` obiekt został już wystawiony. Parametr *PTR* ma ustawioną wartość **`nullptr`** .

- S_OK, jeśli ta operacja zakończy się pomyślnie, ale bieżący `WeakRef` obiekt nie pochodzi od parametru *riid*. Parametr *PTR* ma ustawioną wartość **`nullptr`** . (Aby uzyskać więcej informacji, zobacz uwagi.)

### <a name="remarks"></a>Uwagi

Błąd jest emitowany, jeśli parametr *riid* nie pochodzi od klasy `IInspectable` . Ten błąd zastępuje wartość zwracaną.

Pierwszy szablon jest formularzem, którego należy użyć w kodzie. Drugi szablon (niepokazywany w tym miejscu, ale zadeklarowany w pliku nagłówkowym) jest wewnętrzną specjalizacją pomocnika, która obsługuje funkcje języka C++, takie jak słowo kluczowe odejmowania [autotype.](../../cpp/auto-cpp.md)

Począwszy od zestawu SDK systemu Windows 10, ta metoda nie ustawia `WeakRef` wystąpienia na Jeśli nie można **`nullptr`** uzyskać słabej referencji, dlatego należy unikać sprawdzania błędów kodu, który sprawdza, czy `WeakRef` **`nullptr`** . Zamiast tego zaznacz *ptr* pole PTR **`nullptr`** .

## <a name="weakrefcopyto-method"></a><a name="copyto"></a>WeakRef:: CopyTo, Metoda

Przypisuje wskaźnik do interfejsu, jeśli jest dostępny, do określonej zmiennej wskaźnika.

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
Wskaźnik do `IInspectable` interfejsu. Błąd jest emitowany, jeśli element *U* nie pochodzi od elementu `IInspectable` .

*riid*<br/>
Identyfikator interfejsu. Błąd jest emitowany, jeśli *riid* nie pochodzi od klasy `IWeakReference` .

*ptr*<br/>
Bezpośredni wskaźnik pośredni do `IInspectable` lub `IWeakReference` .

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wartość HRESULT, która opisuje awarię. Aby uzyskać więcej informacji, zobacz **uwagi**.

### <a name="remarks"></a>Uwagi

Wartość zwracana S_OK oznacza, że ta operacja zakończyła się powodzeniem, ale nie wskazuje, czy słabe odwołanie zostało rozpoznane jako silne odwołanie. Jeśli S_OK jest zwracana, należy sprawdzić, czy parametr *p* jest silną referencją; oznacza to, że parametr *p* nie jest równy **`nullptr`** .

Począwszy od zestawu SDK systemu Windows 10, ta metoda nie ustawia `WeakRef` wystąpienia na Jeśli nie można **`nullptr`** uzyskać słabej referencji, dlatego należy unikać błędów podczas sprawdzania kodu, który sprawdza, `WeakRef` czy **`nullptr`** . Zamiast tego zaznacz *ptr* pole PTR **`nullptr`** .

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a>Operator WeakRef:: operator &amp;

Zwraca `ComPtrRef` obiekt, który reprezentuje bieżący `WeakRef` obiekt.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Wartość zwracana

`ComPtrRef`Obiekt, który reprezentuje bieżący `WeakRef` obiekt.

### <a name="remarks"></a>Uwagi

Jest to wewnętrzny operator pomocnika, który nie jest przeznaczony do użycia w kodzie.

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a>WeakRef:: WeakRef — Konstruktor

Inicjuje nowe wystąpienie klasy `WeakRef`.

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
Wskaźnik, odwołanie lub rvalue odwołanie do istniejącego obiektu, który inicjuje bieżący `WeakRef` obiekt.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje pusty `WeakRef` obiekt. Drugi Konstruktor inicjuje `WeakRef` obiekt ze wskaźnika do `IWeakReference` interfejsu. Trzeci Konstruktor inicjuje `WeakRef` obiekt z odwołania do `ComPtr<IWeakReference>` obiektu. Czwarty i piąty Konstruktor inicjuje `WeakRef` obiekt z innego `WeakRef` obiektu.
