---
title: Operacje bitowe ze znakiem | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ffc5335bb28e619f166a524083937d17a59bb97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="signed-bitwise-operations"></a>Operacje bitowe ze znakiem
**ANSI 3.3** wyniki Operacje bitowe na liczb całkowitych ze znakiem  
  
 Operacje bitowe na liczb całkowitych ze znakiem działa w taki sam jak operacje bitowe na liczb całkowitych bez znaku. Na przykład `-16 & 99` może zostać wyrażona w danych binarnych jako  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 Wynik iloczynu bitowego AND jest 96.  
  
## <a name="see-also"></a>Zobacz też  
 [Liczby całkowite](../c-language/integers.md)