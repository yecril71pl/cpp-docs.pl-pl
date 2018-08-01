---
title: Tablice w wyrażeniach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b792bc02cf620cbd961830a99e35ae0c61898fed
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408693"
---
# <a name="arrays-in-expressions"></a>Tablice w wyrażeniach
Kiedy identyfikator typu tablicowego zostanie wyświetlony w wyrażeniu innych niż `sizeof`, adresu (**&**), lub inicjowania odwołania, jest konwertowany na wskaźnik do pierwszego elementu tablicy. Na przykład:  
  
```cpp 
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 Wskaźnik `psz` wskazuje na pierwszy element tablicy `szError1`. Należy pamiętać, że indeksy tablic, w przeciwieństwie do wskaźników, nie są modyfikowane przez l wartościami. W związku z tym następujące przypisanie jest niedozwolone:  
  
```cpp 
szError1 = psz;  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Tablice](../cpp/arrays-cpp.md)