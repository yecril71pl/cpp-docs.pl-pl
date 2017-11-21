---
title: GOTO (MASM) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: goto
dev_langs: C++
helpviewer_keywords: GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 896d99b2ed4abe2080e646b6a541eb1e489d2b75
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="goto-masm"></a>GOTO (MASM)
Przenosi zestaw zaznaczony wiersz **:***macrolabel*.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
GOTO   
macrolabel  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Przejdź do** jest dozwolona tylko wewnątrz [makro](../../assembler/masm/macro.md), [dla](../../assembler/masm/for-masm.md), [forc —](../../assembler/masm/forc.md), [Powtórz](../../assembler/masm/repeat.md), i **podczas**bloków. Etykieta musi być tylko dyrektywy w wierszu i musi być poprzedzony znakiem dwukropka wiodące.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)