---
title: RaiseException — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 0a1c661378c4b71378456f2813159b7415cf3fad
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787452"
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

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)