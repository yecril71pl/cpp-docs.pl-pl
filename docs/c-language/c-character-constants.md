---
title: Stałe znakowe języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0009f795936da7eb0c2ff69aa192e8f609638d2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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