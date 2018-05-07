---
title: Kompilatora (poziom 4) ostrzeżenie C4740 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4740
dev_langs:
- C++
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6260a923da9f48b869707480d64f9be13ef7e9c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4740"></a>Kompilator C4740 ostrzegawcze (poziom 4)
Przepływ wejścia lub wyjścia wbudowanego kodu asemblera pomija optymalizację globalną  
  
 Gdy istnieje skoku w do lub z `asm` bloku, optymalizacje globalne są wyłączone dla tej funkcji.  
  
 Poniższy przykład generuje C4740:  
  
```  
// C4740.cpp  
// compile with: /O2 /W4  
// processor: x86  
int main() {  
   __asm jmp tester  
   tester:;  
}  
```