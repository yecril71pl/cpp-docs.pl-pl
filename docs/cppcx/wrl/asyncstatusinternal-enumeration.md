---
title: AsyncStatusInternal — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: 0eadd1e3a287feecd36b00b231b42c31218352c1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214152"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal — Wyliczenie

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>Uwagi

Określa mapowanie między wyliczeniem wewnętrznym dla stanu operacji asynchronicznych i wyliczeniem `Windows::Foundation::AsyncStatus`.

## <a name="members"></a>Members

`_Created`<br/>
Równoważne `::Windows::Foundation::AsyncStatus::Created`

`_Started`<br/>
Równoważne `::Windows::Foundation::AsyncStatus::Started`

`_Completed`<br/>
Równoważne `::Windows::Foundation::AsyncStatus::Completed`

`_Cancelled`<br/>
Równoważne `::Windows::Foundation::AsyncStatus::Cancelled`

`_Error`<br/>
Równoważne `::Windows::Foundation::AsyncStatus::Error`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Async. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)
