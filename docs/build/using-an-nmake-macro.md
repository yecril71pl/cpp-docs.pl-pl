---
title: Korzystanie z makro NMAKE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6bf098a3723aa7b067b8192bf503975998e4e98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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