---
title: "Stałe znakowe języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 70525e774ea7c89cbd767b607a142d338b797df3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-character-constants"></a>Stałe znakowe języka C
"Stała znakowa" jest tworzony przez otaczającej pojedynczy znak ze znakiem można przedstawić w pojedynczym cudzysłowie (**""**). Stałe znakowe są używane do reprezentowania znaków [zestaw znaków wykonania](../c-language/execution-character-set.md).  
  
## <a name="syntax"></a>Składnia  
 *Stała znakowa*:  
 **"** *c char sekwencji* **"**  
  
 **L "** *c char sekwencji* **"**  
  
 *c char sekwencji*:  
 *c-char*  
  
 *c char sekwencji c-char*  
  
 *c-char*:  
 Każdy członek znak źródłowy ustawić z wyjątkiem pojedynczego cudzysłowu (**"**), ukośnik odwrotny (**\\**), lub znakiem nowego wiersza  
  
 *sekwencja specjalna*  
  
 *sekwencja specjalna*:  
 *prosty sekwencji unikowych*  
  
 *ósemkową sekwencja ucieczki*  
  
 *szesnastkowa sekwencja*  
  
 *prosty sekwencji unikowych*: jeden z  
 **\a \b \f \n \r \t \v**  
  
 **\\' \\" \\\ \\?**  
  
 *ósemkową sekwencja ucieczki*:  
 **\\**  *ósemkowego*  
  
 **\\**  *ósemkowego ósemkowego*  
  
 **\\**  *ósemkowego ósemkowego ósemkowego*  
  
 *szesnastkowa Sekwencja*:  
 **\x***cyfrę szesnastkową*   
  
 *szesnastkowa sekwencja szesnastkowy cyfrowy*  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe języka C](../c-language/c-constants.md)