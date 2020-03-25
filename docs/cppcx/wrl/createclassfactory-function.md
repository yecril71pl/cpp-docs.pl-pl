---
title: CreateClassFactory — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 0467a9a1341e29a61a3b32d999769b01385f641f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214061"
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

*znaczników*<br/>
Kombinacja co najmniej jednej wartości wyliczenia [RuntimeClassType —](runtimeclasstype-enumeration.md) .

*entry*<br/>
Wskaźnik do [CreatorMap](creatormap-structure.md) , który zawiera informacje o inicjacji i rejestracji parametru *riid*.

*riid*<br/>
Odwołanie do identyfikatora interfejsu.

*ppFactory*<br/>
Jeśli ta operacja zakończy się pomyślnie, wskaźnik do fabryki klas.

## <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

## <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowany, jeśli *fabryka* parametrów szablonu nie pochodzi od `IClassFactory`interfejsu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers::Details, przestrzeń nazw](microsoft-wrl-wrappers-details-namespace.md)
