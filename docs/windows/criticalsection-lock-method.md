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
ms.openlocfilehash: 4fedde29441c9c14b68dec5cff998be57d216e29
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607663"
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

*CS*  
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