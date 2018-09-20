---
title: ActivationFactory::GetIids, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 0983d709-d155-4d65-aae4-5b2c8bb0fede
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 89cebd5c6fdfa3ee523a3ab2730ba11c1e2b68ab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407624"
---
# <a name="activationfactorygetiids-method"></a>ActivationFactory::GetIids — Metoda

Pobiera tablicę zaimplementowanego interfejsu identyfikatorów.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount*<br/>
Po zakończeniu tej operacji, liczba identyfikatorów interfejsu w *IID* tablicy.

*IID*<br/>
Po zakończeniu tej operacji, tablicę implementowane identyfikatorów interfejsu.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd. E_OUTOFMEMORY jest możliwe błąd HRESULT.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[ActivationFactory, klasa](../windows/activationfactory-class.md)