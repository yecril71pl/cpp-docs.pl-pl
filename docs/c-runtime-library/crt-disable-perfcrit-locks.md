---
title: "_CRT_DISABLE_PERFCRIT_LOCKS — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
dev_langs: C++
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bb9a5662b15e6e4d0b6df09520263528f9fa72c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS
Wyłącza blokowanie krytyczne wydajności w ramach operacji We/Wy.  
  
## <a name="syntax"></a>Składnia  
  
```  
#define _CRT_DISABLE_PERFCRIT_LOCKS  
```  
  
## <a name="remarks"></a>Uwagi  
 Definiowanie tego symbolu może poprawić wydajność w jednowątkowym programy I/E-granica, powodując, że wszystkie operacje We/Wy założenie modelu jednowątkowe we/wy. Aby uzyskać więcej informacji, zobacz [wydajność bibliotek wielowątkowych](../c-runtime-library/multithreaded-libraries-performance.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe globalne](../c-runtime-library/global-constants.md)