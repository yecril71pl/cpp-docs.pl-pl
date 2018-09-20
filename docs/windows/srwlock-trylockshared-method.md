---
title: SRWLock::TryLockShared, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
dev_langs:
- C++
helpviewer_keywords:
- TryLockShared method
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 985629f224f199d1b1f095847e64cc67fa5a97f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388471"
---
# <a name="srwlocktrylockshared-method"></a>SRWLock::TryLockShared — Metoda

Próbuje pobrać **SRWLock** obiektu w tryb udostępniania dla bieżącej lub określonej **SRWLock** obiektu.

## <a name="syntax"></a>Składnia

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Wskaźnik do **SRWLock** obiektu.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **SRWLock** obiektu w tryb udostępniania i Wątek wywołujący przejmuje na własność blokadę. W przeciwnym razie **SRWLock** obiektu, którego stan jest nieprawidłowy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[SRWLock, klasa](../windows/srwlock-class.md)