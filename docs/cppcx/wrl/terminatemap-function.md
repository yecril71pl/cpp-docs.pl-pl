---
title: TerminateMap — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 2a451bf68bfb543ee5e82a9a48097cac7e8a9821
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026650"
---
# <a name="terminatemap-function"></a>TerminateMap — Funkcja

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>Parametry

*moduł*<br/>
A [modułu](module-class.md).

*serverName*<br/>
Nazwa podzbiór fabryki klas w module, który został określony przez parametr *modułu*.

*forceTerminate*<br/>
**wartość true,** zakończenie klasy fabryk, niezależnie od ich są aktywne; **false** nie zakończyć fabryki klas, jeśli wszystkie fabryki jest aktywny.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** gdyby zakończone; w przeciwnym razie wszystkie fabryki klas **false**.

## <a name="remarks"></a>Uwagi

Zamyka fabryki klas w określonym module.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Details — Przestrzeń nazw](microsoft-wrl-details-namespace.md)