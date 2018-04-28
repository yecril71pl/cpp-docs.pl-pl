---
title: GOTO (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9eecdab2fe91de0aae656b37c6fddafe658e60c0
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="goto-masm"></a>GOTO (MASM)
Przenosi zestaw zaznaczony wiersz **: *** macrolabel*.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
GOTO   
macrolabel  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Przejdź do** jest dozwolona tylko wewnątrz [makro](../../assembler/masm/macro.md), [dla](../../assembler/masm/for-masm.md), [forc —](../../assembler/masm/forc.md), [Powtórz](../../assembler/masm/repeat.md), i **podczas**bloków. Etykieta musi być tylko dyrektywy w wierszu i musi być poprzedzony znakiem dwukropka wiodące.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)