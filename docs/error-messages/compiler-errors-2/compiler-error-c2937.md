---
title: C2937 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2937
dev_langs:
- C++
helpviewer_keywords:
- C2937
ms.assetid: 95671ca3-79f7-4b56-a5f2-a92296da1629
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4972c57963801419be08e60354a9464350cb6ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2937"></a>C2937 błąd kompilatora
"class": typ klasy identyfikator ponownie zdefiniować jako globalny typedef  
  
 Klasy ogólne lub szablonu nie można użyć jako globalną `typedef`.  
  
 Poniższy przykład generuje C2937:  
  
```  
// C2937.cpp  
// compile with: /c  
template<class T>   
struct TC { };  
typedef int TC<int>;   // C2937  
typedef TC<int> c;   // OK  
```  
  
 C2937 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2937b.cpp  
// compile with: /clr  
generic<class T>  
ref struct GC { };  
typedef int GC<int>;   // C2937  
typedef GC<int> xx;   // OK  
```