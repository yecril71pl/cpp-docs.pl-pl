---
title: RaiseException — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 3270057bf5b1b27a98bef1ab236291eab15d27ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213632"
---
# <a name="raiseexception-function"></a>RaiseException — Funkcja

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>Parametry

*wysoki*<br/>
Kod wyjątku dla zgłoszonego wyjątku; oznacza to, że HRESULT operacji zakończonej niepowodzeniem.

*dwExceptionFlags*<br/>
Flaga wskazująca ciągły wyjątek (wartość flagi to zero) lub wyjątek nieciągły (wartość flagi jest różna od zera). Domyślnie wyjątek nie jest ciągły.

## <a name="remarks"></a>Uwagi

Wywołuje wyjątek w wątku wywołującym.

Aby uzyskać więcej informacji, zobacz Funkcja `RaiseException` systemu Windows.

## <a name="requirements"></a>Wymagania

**Nagłówek:** Internal. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)
