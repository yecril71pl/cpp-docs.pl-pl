---
title: ActivationFactoryCallback — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 0be4bebcc561cdf1df3f2502c8cc1927bdc65564
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214217"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback — Funkcja

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>Parametry

*activationId — Członek*<br/>
Dojście do ciągu, który określa nazwę klasy środowiska uruchomieniowego.

*ppFactory*<br/>
Po zakończeniu tej operacji fabryka aktywacji odpowiada parametrowi *activationId — Członek*.

## <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wartość HRESULT, która opisuje awarię. Możliwe niepowodzenia HRESULT to CLASS_E_CLASSNOTAVAILABLE i E_INVALIDARG.

## <a name="remarks"></a>Uwagi

Pobiera fabrykę aktywacji dla określonego identyfikatora aktywacji.

Środowisko wykonawcze systemu Windows wywołuje tę funkcję wywołania zwrotnego, aby zażądać obiektu określonego przez jego nazwę klasy środowiska uruchomieniowego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)
