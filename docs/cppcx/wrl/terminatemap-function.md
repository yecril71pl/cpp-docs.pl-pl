---
title: TerminateMap — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 560f563e43fc8b818b04cd0bda6b01fbc916cb84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213554"
---
# <a name="terminatemap-function"></a>TerminateMap — Funkcja

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>Parametry

*module*<br/>
[Moduł](module-class.md).

*serverName*<br/>
Nazwa podzbioru fabryk klasy w module określonym przez *moduł*parametrów.

*forceTerminate*<br/>
**wartość true** powoduje zakończenie fabryk klasy niezależnie od ich aktywności. **wartość false** , aby nie kończyć fabryk klas, jeśli jakakolwiek fabryka jest aktywna.

## <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli wszystkie fabryki klas zostały zakończone; w przeciwnym razie **false**.

## <a name="remarks"></a>Uwagi

Zamyka fabryki klas w określonym module.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)
