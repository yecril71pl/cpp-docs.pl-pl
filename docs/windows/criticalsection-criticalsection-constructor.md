---
title: "Criticalsection::criticalsection — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs: C++
helpviewer_keywords: CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 532a7b2e046bbdb64db118741a939dadb049f081
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection — Konstruktor
Inicjuje obiekt synchronizacji, który jest podobny do obiektu mutex, ale mogą być używane przez wątki tylko jednego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `spincount`  
 Spin liczbę elementów w obiekcie sekcja krytyczna. Wartość domyślna to 0.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat sekcje krytyczne i spincounts, zobacz **InitializeCriticalSectionAndSpinCount** funkcji w sekcji synchronizacja dokumentacja interfejsu API systemu Windows zawiera.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [CriticalSection, klasa](../windows/criticalsection-class.md)
