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
ms.openlocfilehash: 681f5a64c3e2902c66facbd4f0ac3a3663a7e79d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374255"
---
# <a name="weakref-class"></a>WeakRef — Klasa

Reprezentuje *słabe odwołanie,* które mogą być używane tylko przez środowisko wykonawcze systemu Windows, a nie klasyczny COM. Słabe odwołanie reprezentuje obiekt, który może lub może nie być dostępny.

## <a name="syntax"></a>Składnia

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[WeakRef::WeakRef, konstruktor](#weakref)|Inicjuje nowe wystąpienie klasy `WeakRef`.|
|[WeakRef::~WeakRef, destruktor](#tilde-weakref)|Deinitializes bieżące wystąpienie `WeakRef` klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[WeakRef::As, metoda](#as)|Ustawia określony `ComPtr` parametr wskaźnika do reprezentowania określonego interfejsu.|
|[WeakRef::AsIID, metoda](#asiid)|Ustawia określony `ComPtr` parametr wskaźnika reprezentujący określony identyfikator interfejsu.|
|[WeakRef::CopyTo, metoda](#copyto)|Przypisuje wskaźnik do interfejsu, jeśli jest dostępny, do określonej zmiennej wskaźnika.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator WeakRef::operator&](#operator-ampersand-operator)|Zwraca `ComPtrRef` obiekt reprezentujący `WeakRef` bieżący obiekt.|

## <a name="remarks"></a>Uwagi

Obiekt `WeakRef` zachowuje *silne odwołanie*, które jest skojarzone z obiektem i może być prawidłowe lub nieprawidłowe. Wywołanie `As()` `AsIID()` metody lub, aby uzyskać silne odwołanie. Gdy silne odwołanie jest prawidłowe, może uzyskać dostęp do skojarzonego obiektu. Gdy silne odwołanie jest`nullptr`nieprawidłowe ( ), skojarzony obiekt jest niedostępny.

Obiekt `WeakRef` jest zazwyczaj używany do reprezentowania obiektu, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład skonstruować `WeakRef` obiekt z odwołania do obiektu pliku. Gdy plik jest otwarty, silne odwołanie jest prawidłowe. Ale jeśli plik jest zamknięty, silne odwołanie staje się nieprawidłowe.

Należy zauważyć, że w metodach [As](#as), [AsIID](#asiid) i [CopyTo](#copyto) w windows 10 SDK występuje zmiana zachowania. Wcześniej, po wywołaniu dowolnej z tych `WeakRef` metod, można sprawdzić for, `nullptr` aby ustalić, czy silne odwołanie zostało pomyślnie uzyskane, jak w poniższym kodzie:

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

Powyższy kod nie działa podczas korzystania z systemu Windows 10 SDK (lub nowszego). Zamiast tego sprawdź wskaźnik, który `nullptr`został przekazany do .

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

**Obszar nazw:** Microsoft::WRL

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a>WeakRef::~WeakRef Destructor

Deinitializes bieżące wystąpienie `WeakRef` klasy.

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a>WeakRef::Jako metoda

Ustawia określony `ComPtr` parametr wskaźnika do reprezentowania określonego interfejsu.

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

*Ptr*<br/>
Po zakończeniu tej operacji obiekt reprezentujący parametr *U*.

### <a name="return-value"></a>Wartość zwracana

- S_OK, jeśli ta operacja zakończy się pomyślnie; w przeciwnym razie HRESULT, który wskazuje przyczynę operacji nie `nullptr`powiodło się, a *ptr* jest ustawiona na .

- S_OK, jeśli ta operacja zakończy się `WeakRef` pomyślnie, ale bieżący obiekt został już zwolniony. Parametr *ptr* jest `nullptr`ustawiony na .

- S_OK, jeśli ta operacja zakończy się `WeakRef` pomyślnie, ale bieżący obiekt nie jest pochodną *parametru U*. Parametr *ptr* jest `nullptr`ustawiony na .

### <a name="remarks"></a>Uwagi

Błąd jest emitowany, *U* jeśli `IWeakReference`parametr U jest lub `IInspectable`nie pochodzi od .

Pierwszy szablon jest formularz, który należy użyć w kodzie. Drugi szablon jest wewnętrzna, pomocnicza specjalizacja, która [auto](../../cpp/auto-cpp.md) obsługuje funkcje języka C++, takie jak słowo kluczowe auto-dedukcji typu.

Począwszy od zestawu Windows 10 SDK, `WeakRef` ta `nullptr` metoda nie ustawia wystąpienia, jeśli nie można uzyskać słabeodwoły, więc należy unikać sprawdzania błędów kod, który sprawdza `WeakRef` for `nullptr`. Zamiast tego sprawdź *ptr* dla `nullptr`.

## <a name="weakrefasiid-method"></a><a name="asiid"></a>WeakRef::Metoda AsiID

Ustawia określony `ComPtr` parametr wskaźnika reprezentujący określony identyfikator interfejsu.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Identyfikator interfejsu.

*Ptr*<br/>
Po zakończeniu tej operacji obiekt reprezentujący parametr *riid*.

### <a name="return-value"></a>Wartość zwracana

- S_OK, jeśli ta operacja zakończy się pomyślnie; w przeciwnym razie HRESULT, który wskazuje przyczynę operacji nie `nullptr`powiodło się, a *ptr* jest ustawiona na .

- S_OK, jeśli ta operacja zakończy się `WeakRef` pomyślnie, ale bieżący obiekt został już zwolniony. Parametr *ptr* jest `nullptr`ustawiony na .

- S_OK, jeśli ta operacja zakończy się `WeakRef` pomyślnie, ale bieżący obiekt nie jest pochodną *parametru riid*. Parametr *ptr* jest `nullptr`ustawiony na . (Aby uzyskać więcej informacji, zobacz Uwagi).)

### <a name="remarks"></a>Uwagi

Błąd jest emitowany, jeśli parametr *riid* `IInspectable`nie pochodzi od . Ten błąd zastępuje wartość zwracaną.

Pierwszy szablon jest formularz, który należy użyć w kodzie. Drugi szablon (nie pokazano w tym miejscu, ale zadeklarowane w pliku nagłówka) jest wewnętrzna, specjalizacja pomocnika, który obsługuje funkcje języka C++, takie jak słowo kluczowe [auto](../../cpp/auto-cpp.md) potrącenie typu.

Począwszy od zestawu Windows 10 SDK, `WeakRef` ta `nullptr` metoda nie ustawia wystąpienia, jeśli nie można uzyskać słabeodwoły, więc należy unikać sprawdzania błędów kod, który sprawdza `WeakRef` for `nullptr`. Zamiast tego sprawdź *ptr* dla `nullptr`.

## <a name="weakrefcopyto-method"></a><a name="copyto"></a>WeakRef::Metoda CopyTo

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
Wskaźnik `IInspectable` interfejsu. Błąd jest emitowany, jeśli *U* nie `IInspectable`pochodzi od .

*Riid*<br/>
Identyfikator interfejsu. Błąd jest emitowany, jeśli *riid* nie `IWeakReference`pochodzi od .

*Ptr*<br/>
Wskaźnik podwójnie pośredni do `IInspectable` `IWeakReference`lub .

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który opisuje błąd. Aby uzyskać więcej informacji, zobacz **Uwagi**.

### <a name="remarks"></a>Uwagi

Zwracana wartość S_OK oznacza, że ta operacja powiodła się, ale nie wskazuje, czy słabe odwołanie zostało rozpoznane do silnego odwołania. Jeśli zwracany jest S_OK, sprawdź, czy parametr *p* jest silnym odniesieniem; oznacza to, *p* że parametr p `nullptr`nie jest równy .

Począwszy od zestawu Windows 10 SDK, `WeakRef` ta `nullptr` metoda nie ustawia wystąpienia, jeśli nie można uzyskać słabeodwoły, więc należy unikać sprawdzania błędów kod, który sprawdza `WeakRef` for `nullptr`. Zamiast tego sprawdź *ptr* dla `nullptr`.

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a>WeakRef::operator&amp; Operator

Zwraca `ComPtrRef` obiekt reprezentujący `WeakRef` bieżący obiekt.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, `ComPtrRef` który reprezentuje `WeakRef` bieżący obiekt.

### <a name="remarks"></a>Uwagi

Jest to wewnętrzny operator pomocnika, który nie jest przeznaczony do użycia w kodzie.

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a>WeakRef::WeakRef Konstruktor

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

*Ptr*<br/>
Wskaźnik, odwołanie lub odwołanie do wartości do istniejącego obiektu, który `WeakRef` inicjuje bieżący obiekt.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje pusty `WeakRef` obiekt. Drugi konstruktor inicjuje `WeakRef` obiekt ze `IWeakReference` wskaźnika do interfejsu. Trzeci konstruktor inicjuje `WeakRef` obiekt z `ComPtr<IWeakReference>` odwołania do obiektu. Konstruktory czwarty i piąty `WeakRef` inicjuje obiekt z innego `WeakRef` obiektu.
