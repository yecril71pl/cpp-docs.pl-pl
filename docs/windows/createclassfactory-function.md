---
title: Createclassfactory — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
dev_langs:
- C++
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3cecffa8505aaead738007e2a0872c3f1bc5a6d6
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593651"
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

*flagi*  
Kombinacji jednego lub więcej [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) wartości wyliczenia.

*entry*  
Wskaźnik do [creatormap —](../windows/creatormap-structure.md) zawierający informacje o parametrze inicjowania i rejestracji *riid*.

*Parametr riid*  
Odwołanie do identyfikatora interfejsu.

*ppFactory*  
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