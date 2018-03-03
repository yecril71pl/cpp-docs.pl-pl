---
title: "Tablice w wyrażeniach | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29f6e16e665d8076ed5a1fe593e1bb9437f1406a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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