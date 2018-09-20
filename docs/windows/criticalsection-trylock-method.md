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
ms.openlocfilehash: 44b4e251898ef6386d0642582af2c00881f7a181
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408586"
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

*CS*<br/>
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