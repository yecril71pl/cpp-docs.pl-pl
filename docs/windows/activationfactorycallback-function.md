---
title: ActivationFactoryCallback — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 8da0f3f54e142673a44909f3fe2141b09a71d388
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586449"
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