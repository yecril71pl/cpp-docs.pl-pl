---
title: Operacje bitowe ze znakiem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3ddd1c32beb5660fd1fa3c0160756734b4c1923
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385260"
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