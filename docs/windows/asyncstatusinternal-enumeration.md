---
title: Asyncstatusinternal — wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs:
- C++
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b389e5b137ef3cdb94ffbb1fc381ebe2e5813963
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603973"
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

`_Created`  
Wartość równoważna `::Windows::Foundation::AsyncStatus::Created`

`_Started`  
Wartość równoważna `::Windows::Foundation::AsyncStatus::Started`

`_Completed`  
Wartość równoważna `::Windows::Foundation::AsyncStatus::Completed`

`_Cancelled`  
Wartość równoważna `::Windows::Foundation::AsyncStatus::Cancelled`

`_Error`  
Wartość równoważna `::Windows::Foundation::AsyncStatus::Error`

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)