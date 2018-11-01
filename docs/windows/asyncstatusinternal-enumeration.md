---
title: AsyncStatusInternal — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: fe70ee1ac5d26ed15d2b497356fe941c72ec0c83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564947"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal — Wyliczenie

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>Uwagi

Określa mapowanie między wewnętrznego wyliczenia stanu operacji asynchronicznych i `Windows::Foundation::AsyncStatus` wyliczenia.

## <a name="members"></a>Elementy członkowskie

`_Created`<br/>
Wartość równoważna `::Windows::Foundation::AsyncStatus::Created`

`_Started`<br/>
Wartość równoważna `::Windows::Foundation::AsyncStatus::Started`

`_Completed`<br/>
Wartość równoważna `::Windows::Foundation::AsyncStatus::Completed`

`_Cancelled`<br/>
Wartość równoważna `::Windows::Foundation::AsyncStatus::Cancelled`

`_Error`<br/>
Wartość równoważna `::Windows::Foundation::AsyncStatus::Error`

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)