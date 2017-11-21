---
title: Podstawianie makr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d8e63e071629c2647ccd8f89095fbc7c2285f1a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="macro-substitution"></a>Podstawianie makr
Gdy *makra* zostanie wywołany, każde wystąpienie *ciąg1* w swojej definicji zastępuje ciąg *ciąg2*.  
  
## <a name="syntax"></a>Składnia  
  
```  
$(macroname:string1=string2)  
```  
  
## <a name="remarks"></a>Uwagi  
 Podstawianie makr jest uwzględniana wielkość liter i jest literałem; *ciąg1* i *ciąg2* nie można wywołać makra. Podstawienia nie modyfikuje oryginalnej definicji. Można zastąpić tekst w dowolnym wstępnie zdefiniowanego makra, z wyjątkiem [ $$@ ](../build/filename-macros.md).  
  
 Bez spacji i karty poprzedzać colon; wszelkie po dwukropku są interpretowane jako literału. Jeśli *ciąg2* jest null, wszystkie wystąpienia *ciąg1* są usuwane z ciągu definicji makra.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z makro NMAKE](../build/using-an-nmake-macro.md)