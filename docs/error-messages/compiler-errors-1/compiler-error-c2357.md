---
title: "C2357 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2357
dev_langs: C++
helpviewer_keywords: C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b3804f0ee55284aabcd46b0f45c557ccc79cbb8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2357"></a>C2357 błąd kompilatora
"identyfikator": musi być funkcją typu "type"  
  
 Kod deklaruje wersję `atexit` funkcja, która nie jest zgodna z wersją zadeklarowany wewnętrznie przez kompilator. Deklarowanie `atexit` w następujący sposób:  
  
```  
int __cdecl atexit(void (__cdecl *)());  
```  
  
 Aby uzyskać więcej informacji, zobacz [init_seg](../../preprocessor/init-seg.md).  
  
 Poniższy przykład generuje C2357:  
  
```  
// C2357.cpp  
// compile with: /c  
// C2357 expected  
#pragma warning(disable : 4075)  
// Uncomment the following line to resolve.  
// int __cdecl myexit(void (__cdecl *)());  
#pragma init_seg(".mine$m",myexit)  
```