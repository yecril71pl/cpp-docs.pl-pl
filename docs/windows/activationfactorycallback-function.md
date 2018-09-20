---
title: Activationfactorycallback — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 62efb2b1aa2cd2caa0c5701696689ea3df19f962
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443621"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback — Funkcja

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>Parametry

*activationid —*<br/>
Obsługa na ciąg, który określa nazwę klasy środowiska uruchomieniowego.

*ppFactory*<br/>
Po zakończeniu tej operacji, fabryką aktywacji, który odpowiada parametrowi *activationid —*.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd. Prawdopodobnie niepowodzenie HRESULTs są CLASS_E_CLASSNOTAVAILABLE i E_INVALIDARG.

## <a name="remarks"></a>Uwagi

Pobiera fabrykę aktywacji dla identyfikatora określonego aktywacji.

Środowisko wykonawcze Windows wywołuje tę funkcję wywołania zwrotnego, aby zażądać obiektu określonego przez nazwę klasy środowiska uruchomieniowego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)