---
title: CreateClassFactory — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: aa235312e39434e39ea954aa083701fa55f336ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484035"
---
# <a name="createclassfactory-function"></a>CreateClassFactory — Funkcja

Tworzy fabrykę, która tworzy wystąpienia określonej klasy.

## <a name="syntax"></a>Składnia

```cpp
template<typename Factory>
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(
   _In_ unsigned int *flags,
   _In_ const CreatorMap* entry,
   REFIID riid,
   _Outptr_ IUnknown **ppFactory
) throw();
```

### <a name="parameters"></a>Parametry

*flagi*<br/>
Kombinacji jednego lub więcej [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) wartości wyliczenia.

*entry*<br/>
Wskaźnik do [creatormap —](../windows/creatormap-structure.md) zawierający informacje o parametrze inicjowania i rejestracji *riid*.

*Parametr riid*<br/>
Odwołanie do identyfikatora interfejsu.

*ppFactory*<br/>
Jeśli operacja zakończy się pomyślnie, wskaźnik do fabryki klas.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowane, jeśli parametr szablonu *fabryki* nie pochodzi z interfejsu `IClassFactory`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers::Details, przestrzeń nazw](../windows/microsoft-wrl-wrappers-details-namespace.md)