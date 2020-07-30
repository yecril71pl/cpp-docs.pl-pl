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
ms.openlocfilehash: 9a367a61a029abe1be599b1e262e279402149ccd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220460"
---
# <a name="weakreference-class"></a>WeakReference — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
class WeakReference;
```

## <a name="remarks"></a>Uwagi

Reprezentuje *słabe odwołanie* , które może być używane z środowisko wykonawcze systemu Windows lub klasycznego modelu com. Słabe odwołanie reprezentuje obiekt, który może lub nie jest dostępny.

`WeakReference`Obiekt zachowuje *silną referencję*, która jest wskaźnikiem do obiektu i *silną liczbę odwołań*, czyli liczbę kopii silnego odwołania, które zostały rozdzielone przez `Resolve()` metodę. Gdy silna liczba odwołań jest różna od zera, silne odwołanie jest prawidłowe i dostęp do obiektu. Gdy silna liczba odwołań będzie równa zero, silne odwołanie jest nieprawidłowe i obiekt jest niedostępny.

`WeakReference`Obiekt jest zazwyczaj używany do reprezentowania obiektu, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład konstruowanie `WeakReference` obiektu z odwołania do obiektu pliku. Gdy plik jest otwarty, silne odwołanie jest prawidłowe. Ale jeśli plik jest zamknięty, silne odwołanie jest nieprawidłowe.

`WeakReference`Metody są bezpieczne wątkowo.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference:: WeakReference](#weakreference)        | Inicjuje nowe wystąpienie klasy `WeakReference`.
[WeakReference:: ~ WeakReference](#tilde-weakreference) | Deinitializes (niszczy) bieżące wystąpienie `WeakReference` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                                 | Opis
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::D ecrementStrongReference](#decrementstrongreference) | Zmniejsza silną liczbę odwołań bieżącego `WeakReference` obiektu.
[WeakReference:: IncrementStrongReference —](#incrementstrongreference) | Zwiększa silną liczbę odwołań bieżącego `WeakReference` obiektu.
[WeakReference:: Rozwiąż](#resolve)                                   | Ustawia określony wskaźnik na bieżącą silną wartość odniesienia, jeśli silna liczba odwołań jest różna od zera.
[WeakReference:: unknown](#setunknown)                             | Ustawia silną referencję bieżącego `WeakReference` obiektu do określonego wskaźnika interfejsu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WeakReference`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>WeakReference:: ~ WeakReference

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Deinicjalizuje bieżące wystąpienie `WeakReference` klasy.

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>WeakReference::D ecrementStrongReference

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Uwagi

Zmniejsza silną liczbę odwołań bieżącego `WeakReference` obiektu.

Gdy silna liczba odwołań będzie równa zero, silne odwołanie jest ustawione na **`nullptr`** .

### <a name="return-value"></a>Wartość zwracana

Zmniejszona silna liczba odwołań.

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>WeakReference:: IncrementStrongReference —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Wartość zwracana

Przyrostowa silna liczba odwołań.

### <a name="remarks"></a>Uwagi

Zwiększa silną liczbę odwołań bieżącego `WeakReference` obiektu.

## <a name="weakreferenceresolve"></a><a name="resolve"></a>WeakReference:: Rozwiąż

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identyfikator interfejsu.

*ppvObject*<br/>
Gdy ta operacja zostanie ukończona, kopia bieżącego silnego odwołania, jeśli silna liczba odwołań jest różna od zera.

### <a name="return-value"></a>Wartość zwracana

- S_OK, jeśli ta operacja zakończyła się pomyślnie, a liczba silnych odwołań wynosi zero. Parametr *ppvObject* jest ustawiony na **`nullptr`** .

- S_OK, jeśli ta operacja zakończyła się pomyślnie, a liczba silnych odwołań jest różna od zera. Parametr *ppvObject* jest ustawiony na silne odwołanie.

- W przeciwnym razie wartość HRESULT wskazuje przyczynę niepowodzenia tej operacji.

### <a name="remarks"></a>Uwagi

Ustawia określony wskaźnik na bieżącą silną wartość odniesienia, jeśli silna liczba odwołań jest różna od zera.

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>WeakReference:: unknown

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Parametry

*unk*<br/>
Wskaźnik do `IUnknown` interfejsu obiektu.

### <a name="remarks"></a>Uwagi

Ustawia silną referencję bieżącego `WeakReference` obiektu do określonego wskaźnika interfejsu.

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>WeakReference:: WeakReference

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
WeakReference();
```

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `WeakReference`.

Wskaźnik silnej referencji dla `WeakReference` obiektu jest zainicjowany do **`nullptr`** , a liczba silnych odwołań jest inicjowana do 1.
