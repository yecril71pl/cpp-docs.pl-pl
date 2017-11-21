---
title: "Tablice w wyrażeniach | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6f4bceac05f72c609c7aef8702c6313572ed6db5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="arrays-in-expressions"></a>Tablice w wyrażeniach
Kiedy identyfikator typu tablicowego zostanie wyświetlony w wyrażeniu innych niż `sizeof`, adresu (**&**), lub inicjowania odwołania, jest konwertowany na wskaźnik do pierwszego elementu tablicy. Na przykład:  
  
```  
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 Wskaźnik `psz` wskazuje pierwszy element macierzy `szError1`. Należy pamiętać, że w przeciwieństwie do wskaźników, tablic nie są modyfikowalną l wartości. W związku z tym następującego przypisania jest niedozwolony:  
  
```  
szError1 = psz;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../cpp/arrays-cpp.md)