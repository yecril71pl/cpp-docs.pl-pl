---
title: CriticalSection::CriticalSection, Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 892a32c6ff6f8e9a3a30452d05dd6e15c38a4fa8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605055"
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection — Konstruktor

Inicjuje obiekt synchronizacji, który jest podobny do obiektu mutex, ale mogą być używane przez wątki tylko pojedynczego procesu.

## <a name="syntax"></a>Składnia

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parametry

*spincount*  
Liczba obiektów sekcję krytyczną pokrętła. Wartość domyślna to 0.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat sekcje krytyczne i spincounts zobacz `InitializeCriticalSectionAndSpinCount` działa w programach **synchronizacji** sekcji zawiera interfejs API Windows.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[CriticalSection, klasa](../windows/criticalsection-class.md)