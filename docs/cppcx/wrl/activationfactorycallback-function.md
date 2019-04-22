---
title: ActivationFactoryCallback — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 4743e7724c5aba4171cb017654267afaac676f24
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021608"
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

*activationId*<br/>
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

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)