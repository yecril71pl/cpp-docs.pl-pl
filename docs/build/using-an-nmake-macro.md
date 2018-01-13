---
title: Korzystanie z makro NMAKE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fc5c6c8851654b1a767967ffc900886d75521130
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-nmake-macro"></a>Korzystanie z makro NMAKE
Aby użyć makra, ujmij jej nazwę w nawiasach poprzedzone znak dolara ($) w następujący sposób.  
  
## <a name="syntax"></a>Składnia  
  
```  
$(macroname)  
```  
  
## <a name="remarks"></a>Uwagi  
 Spacje nie są dozwolone. Nawiasy są opcjonalne, jeśli *makra* jest pojedynczym znakiem. Ciąg definicji zastępuje $(*makra*); zdefiniowane makro zastępuje pusty ciąg.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
 [Podstawianie makr](../build/macro-substitution.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i NMAKE](../build/macros-and-nmake.md)