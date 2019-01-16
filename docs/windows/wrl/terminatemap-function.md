---
title: TerminateMap — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 17d02ea9cade0301798a5d6625f8eb9a568cb2cc
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335023"
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

*module*<br/>
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

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)