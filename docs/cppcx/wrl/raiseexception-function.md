---
title: RaiseException — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 08305c5d59d7e272aac87ad9aa183c8e82588632
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029962"
---
# <a name="raiseexception-function"></a>RaiseException — Funkcja

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>Parametry

*godz.*<br/>
Kod wyjątku wyjątków zgłaszanych; oznacza to, że wartość HRESULT operację zakończoną niepowodzeniem.

*dwExceptionFlags*<br/>
Flaga wskazująca pozwala na kontynuację wyjątek (wartość flagi wynosi zero), lub noncontinuable wyjątek (wartość flagi jest różna od zera). Domyślnie wyjątek jest wystąpieniu.

## <a name="remarks"></a>Uwagi

Zgłasza wyjątek w wątku wywołującego.

Aby uzyskać więcej informacji, zobacz Windows `RaiseException` funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Details — Przestrzeń nazw](microsoft-wrl-details-namespace.md)