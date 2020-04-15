---
title: WeakReference — Klasa
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
ms.openlocfilehash: a80c0ec14da2a955a95ac84dd3975212ef20ae04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374219"
---
# <a name="weakreference-class"></a>WeakReference — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
class WeakReference;
```

## <a name="remarks"></a>Uwagi

Reprezentuje *słabe odwołanie,* które mogą być używane ze czasem wykonywania systemu Windows lub klasycznej com. Słabe odwołanie reprezentuje obiekt, który może lub może nie być dostępny.

Obiekt `WeakReference` zachowuje *silne odniesienie*, który jest wskaźnikiem do obiektu i *silną liczbą odwołań*, która jest liczbą `Resolve()` kopii silnego odwołania, które zostały rozłożone przez metodę. Podczas gdy liczba odwołań silnych jest niezerowa, silne odwołanie jest prawidłowe i obiekt jest dostępny. Gdy liczba silnych odwołań staje się równa zero, silne odwołanie jest nieprawidłowe, a obiekt jest niedostępny.

Obiekt `WeakReference` jest zazwyczaj używany do reprezentowania obiektu, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład skonstruować `WeakReference` obiekt z odwołania do obiektu pliku. Gdy plik jest otwarty, silne odwołanie jest prawidłowe. Ale jeśli plik jest zamknięty, silne odwołanie staje się nieprawidłowe.

Metody `WeakReference` są bezpieczne dla wątków.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference::WeakReference](#weakreference)        | Inicjuje nowe wystąpienie klasy `WeakReference`.
[Słabarefera::~SłabeReferencja](#tilde-weakreference) | Deinitializes (niszczy) bieżące wystąpienie `WeakReference` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                                 | Opis
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::DecrementStrongReference](#decrementstrongreference) | Zmniejsza liczbę silnych odwołań `WeakReference` bieżącego obiektu.
[Zdecydowanie słaby::IncrementStrongReference](#incrementstrongreference) | Zwiększa silną liczbę odwołań `WeakReference` bieżącego obiektu.
[Słabarefera::Rozwiąż](#resolve)                                   | Ustawia określony wskaźnik do bieżącej silnej wartości referencyjnej, jeśli liczba silnych odwołań jest niezerowa.
[SłabeReferencja::SetUnknown](#setunknown)                             | Ustawia silne odwołanie do `WeakReference` bieżącego obiektu na określony wskaźnik interfejsu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WeakReference`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>Słabarefera::~SłabeReferencja

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Deinitializes bieżące wystąpienie `WeakReference` klasy.

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>WeakReference::DecrementStrongReference

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Uwagi

Zmniejsza liczbę silnych odwołań `WeakReference` bieżącego obiektu.

Gdy silna liczba odwołań staje się równa `nullptr`zero, silne odwołanie jest ustawione na .

### <a name="return-value"></a>Wartość zwracana

Zdemalizowana liczba silnych odwołań.

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>Zdecydowanie słaby::IncrementStrongReference

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Wartość zwracana

Przyrostowa liczba silnych odwołań.

### <a name="remarks"></a>Uwagi

Zwiększa silną liczbę odwołań `WeakReference` bieżącego obiektu.

## <a name="weakreferenceresolve"></a><a name="resolve"></a>Słabarefera::Rozwiąż

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Identyfikator interfejsu.

*ppvObiekt*<br/>
Po zakończeniu tej operacji, kopię bieżącego silnego odwołania, jeśli liczba odwołania silnego jest niezerowa.

### <a name="return-value"></a>Wartość zwracana

- S_OK, jeśli ta operacja zakończy się pomyślnie, a liczba silnych odwołań wynosi zero. Parametr *ppvObject* jest `nullptr`ustawiony na .

- S_OK, jeśli ta operacja zakończy się pomyślnie, a liczba silnych odwołań jest niezerowa. Parametr *ppvObject* jest ustawiony na silne odwołanie.

- W przeciwnym razie HRESULT, który wskazuje przyczynę tej operacji nie powiodło się.

### <a name="remarks"></a>Uwagi

Ustawia określony wskaźnik do bieżącej silnej wartości referencyjnej, jeśli liczba silnych odwołań jest niezerowa.

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>SłabeReferencja::SetUnknown

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Parametry

*Unk*<br/>
Wskaźnik do `IUnknown` interfejsu obiektu.

### <a name="remarks"></a>Uwagi

Ustawia silne odwołanie do `WeakReference` bieżącego obiektu na określony wskaźnik interfejsu.

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>WeakReference::WeakReference

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
WeakReference();
```

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `WeakReference`.

Silny wskaźnik odniesienia `WeakReference` dla obiektu jest `nullptr`inicjowany do , a liczba silnych odwołań jest inicjowana do 1.
