---
title: CriticalSection::Lock, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f13af220107ba8d5bc5c26c65c2034f125a39454
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382456"
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock — Metoda

Czeka na własność obiektu określona sekcja krytycznego. Funkcja zwróci, jeśli wątek wywołujący udzielono prawa własności.

## <a name="syntax"></a>Składnia

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*CS*<br/>
Obiekt sekcję krytyczną określonych przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Obiekt blokady, który może służyć do odblokowania bieżąca sekcja krytycznego.

## <a name="remarks"></a>Uwagi

Pierwszy **blokady** funkcji ma wpływ na bieżący obiekt sekcję krytyczną. Drugi **blokady** funkcji ma wpływ na sekcję krytyczną określonych przez użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[CriticalSection, klasa](../windows/criticalsection-class.md)