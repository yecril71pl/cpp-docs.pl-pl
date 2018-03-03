---
title: "C2379 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2379
dev_langs:
- C++
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d39a94722563a9feef7914f092968f1754d0d429
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2379"></a>C2379 błąd kompilatora
Liczba parametrów formalnych jest innego typu kiedy jest zwiększany  
  
 Typ określony parametr nie jest zgodny, za pośrednictwem domyślne promocje, z poziomu typu w poprzedniej deklaracji. Jest to błąd w ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) i ostrzeżenia z rozszerzeniami firmy Microsoft (**/Ze**).  
  
 Poniższy przykład generuje C2379:  
  
```  
// C2379.c  
// compile with: /Za  
void func();  
void func(char);   // C2379, char promotes to int  
```