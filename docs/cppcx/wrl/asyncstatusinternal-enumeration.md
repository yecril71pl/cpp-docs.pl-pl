---
title: AsyncStatusInternal — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: f12bf4aafc87e44a6e2fb15ba79de4a9744bea58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398787"
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

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)