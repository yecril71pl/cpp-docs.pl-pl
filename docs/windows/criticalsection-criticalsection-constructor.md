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
ms.openlocfilehash: f87f95a0683f6b4440d2be8b770902a7e4ecde59
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644297"
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