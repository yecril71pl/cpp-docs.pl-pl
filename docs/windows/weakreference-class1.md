---
title: WeakReference, klasa1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4d82dbffee5b686c6d8923f395c74fedfac54816
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169674"
---
# <a name="weakreference-class1"></a>WeakReference, klasa1

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
class WeakReference;
```

## <a name="remarks"></a>Uwagi

Reprezentuje *słabe odwołanie* które mogą być używane z Windows Runtime lub Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.

A `WeakReference` obiekt zachowuje *silne odwołanie*, który jest wskaźnikiem do obiektu, a *liczba silne odwołanie*, czyli liczbę kopii silne odwołanie, które zostały przekazane przez `Resolve()` metody. Podczas gdy liczba silne odwołanie jest różna od zera, silne odwołanie jest prawidłowy, a obiekt jest dostępny. Gdy liczba silne odwołanie staje się zerem, silne odwołanie jest nieprawidłowe i obiektu jest niedostępny.

A `WeakReference` obiekt jest zwykle używana do reprezentowania obiekt, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład, utworzyć `WeakReference` obiektu z odwołaniem do obiektu pliku. Gdy plik jest otwarty, silne odwołanie jest prawidłowy. Ale jeśli ten plik będzie zamknięty, silne odwołanie staje się nieprawidłowy.

`WeakReference` Metody są bezpieczne dla wątków.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | ---------------------------------------------------------------------------
[Weakreference::weakreference —](#weakreference)        | Inicjuje nowe wystąpienie klasy `WeakReference` klasy.
[WeakReference:: ~ WeakReference](#tilde-weakreference) | Wyłącza (niszczy) bieżące wystąpienie `WeakReference` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                                 | Opis
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::DecrementStrongReference](#decrementstrongreference) | Dekrementuje silne odwołanie zliczane bieżącego `WeakReference` obiektu.
[WeakReference::IncrementStrongReference](#incrementstrongreference) | Zwiększa liczbę silne odwołanie bieżącego `WeakReference` obiektu.
[Weakreference::Resolve —](#resolve)                                   | Ustawia określony wskaźnik do bieżącej wartości silne odwołanie, jeśli liczba silne odwołanie jest różna od zera.
[WeakReference::SetUnknown](#setunknown)                             | Ustawia silne odwołanie bieżącego `WeakReference` obiekt określony wskaźnik interfejsu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WeakReference`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="tilde-weakreference"></a>WeakReference:: ~ WeakReference

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Deinicjuje bieżące wystąpienie `WeakReference` klasy.

## <a name="decrementstrongreference"></a>WeakReference::DecrementStrongReference

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Uwagi

Dekrementuje silne odwołanie zliczane bieżącego `WeakReference` obiektu.

Gdy liczba silne odwołanie staje się zerem, silne odwołanie jest równa `nullptr`.

### <a name="return-value"></a>Wartość zwracana

Liczba wraz z przydzielaniem silne odwołanie.

## <a name="incrementstrongreference"></a>WeakReference::IncrementStrongReference

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Wartość zwracana

Liczba zwiększona silne odwołanie.

### <a name="remarks"></a>Uwagi

Zwiększa liczbę silne odwołanie bieżącego `WeakReference` obiektu.

## <a name="resolve"></a>Weakreference::Resolve —

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
STDMETHOD(Resolve)  
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
Identyfikator interfejsu.

*ppvObject*<br/>
Gdy ta operacja zostanie ukończone, kopię bieżącego silne odwołanie, jeśli liczba silne odwołanie jest różna od zera.

### <a name="return-value"></a>Wartość zwracana

- S_OK, jeśli operacja zakończy się pomyślnie, a liczba silne odwołanie ma wartość zero. *PpvObject* parametr ma wartość `nullptr`.

- S_OK, jeśli operacja zakończy się pomyślnie, a liczba silne odwołanie jest różna od zera. *PpvObject* parametr ma wartość silne odwołanie.

- W przeciwnym razie wartość HRESULT, która wskazuje przyczynę tej operacji nie powiodło się.

### <a name="remarks"></a>Uwagi

Ustawia określony wskaźnik do bieżącej wartości silne odwołanie, jeśli liczba silne odwołanie jest różna od zera.

## <a name="setunknown"></a>WeakReference::SetUnknown

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Parametry

*UNK*<br/>
Wskaźnik do `IUnknown` interfejs obiektu.

### <a name="remarks"></a>Uwagi

Ustawia silne odwołanie bieżącego `WeakReference` obiekt określony wskaźnik interfejsu.

## <a name="weakreference"></a>Weakreference::weakreference —

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
WeakReference();
```

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `WeakReference` klasy.

Wskaźnik silne odwołanie dla `WeakReference` obiekt jest inicjowany do `nullptr`, oraz liczba silne odwołanie jest inicjowany do 1.
