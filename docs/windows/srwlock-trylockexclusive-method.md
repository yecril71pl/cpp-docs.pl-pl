---
title: SRWLock::TryLockExclusive, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs:
- C++
helpviewer_keywords:
- TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ec8275b1db692410677276e762f79ccf23548cc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606234"
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive — Metoda

Próbuje pobrać **SRWLock** obiektu w trybie wyłączności dla bieżącej lub określonej **SRWLock** obiektu. Jeśli wywołanie zakończy się pomyślnie, wątek wywołujący przejmuje na własność blokadę.

## <a name="syntax"></a>Składnia

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*  
Wskaźnik do **SRWLock** obiektu.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **SRWLock** obiektu w trybie wyłączności i Wątek wywołujący przejmuje na własność blokadę. W przeciwnym razie **SRWLock** obiektu, którego stan jest nieprawidłowy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[SRWLock, klasa](../windows/srwlock-class.md)