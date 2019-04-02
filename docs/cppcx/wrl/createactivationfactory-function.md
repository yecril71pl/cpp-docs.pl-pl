---
title: CreateActivationFactory — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
ms.openlocfilehash: 07bc0dceb8066faf9c1beab64d48245d8735aa64
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787477"
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory — Funkcja

Tworzy fabrykę, która tworzy wystąpienia określonej klasy, które można uaktywnić przez środowisko wykonawcze Windows.

## <a name="syntax"></a>Składnia

```cpp
template<typename Factory>
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,
      REFIID riid,
   _Outptr_ IUnknown **ppFactory) throw();
```

### <a name="parameters"></a>Parametry

*flagi*<br/>
Kombinacji jednego lub więcej [RuntimeClassType](runtimeclasstype-enumeration.md) wartości wyliczenia.

*entry*<br/>
Wskaźnik do [creatormap —](creatormap-structure.md) zawierający informacje o parametrze inicjowania i rejestracji *riid*.

*Parametr riid*<br/>
Odwołanie do identyfikatora interfejsu.

*ppFactory*<br/>
Jeśli operacja zakończy się pomyślnie, wskaźnik do aktywacji fabryki.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowane, jeśli parametr szablonu *fabryki* nie pochodzi z interfejsu `IActivationFactory`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers::Details, przestrzeń nazw](microsoft-wrl-wrappers-details-namespace.md)