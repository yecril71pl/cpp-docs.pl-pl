---
title: CriticalSection::TryLock, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 382dbdd2d0816d6ab0846acd0f8c164cd542114f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575844"
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock — Metoda

Próbuje wprowadzić sekcję krytyczną bez blokowania. Jeśli wywołanie zakończy się pomyślnie, wątek wywołujący przejmuje na własność sekcję krytyczną.

## <a name="syntax"></a>Składnia

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*CS*  
Obiekt sekcję krytyczną określonych przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli pomyślnie podano sekcję krytyczną lub bieżący wątek jest już właścicielem sekcję krytyczną. Zero, jeśli inny wątek jest już właścicielem sekcję krytyczną.

## <a name="remarks"></a>Uwagi

Pierwszy **trylock —** funkcji ma wpływ na bieżący obiekt sekcję krytyczną. Drugi **trylock —** funkcji ma wpływ na sekcję krytyczną określonych przez użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[CriticalSection, klasa](../windows/criticalsection-class.md)