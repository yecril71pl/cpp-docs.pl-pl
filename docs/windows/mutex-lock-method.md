---
title: Mutex::Lock, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bb04b8be33f81931106574152d0ccb6ba535295
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427839"
---
# <a name="mutexlock-method"></a>Mutex::Lock — Metoda

Czeka, aż do bieżącego obiektu lub **Mutex** obiekt skojarzony z określonym dojściem wersji obiektu mutex lub określony limit czasu upłynął.

## <a name="syntax"></a>Składnia

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>Parametry

*MS*<br/>
Interwał limitu czasu w milisekundach. Wartość domyślna to NIESKOŃCZONE, który oczekuje w nieskończoność.

*h*<br/>
Dojście **Mutex** obiektu.

## <a name="return-value"></a>Wartość zwracana

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[Mutex — klasa](../windows/mutex-class1.md)