---
title: Kompilatora (poziom 1) ostrzeżenie C4311 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4311
dev_langs:
- C++
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba06488ed41e7e296f9f6c16f34af827274acfd4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4311"></a>Kompilator C4311 ostrzegawcze (poziom 1)
'zmienna' : obcinanie wskaźnika z 'typ do 'typ'  
  
 To ostrzeżenie wykrywa problemy obcięcie wskaźnika 64-bitowych. Na przykład, jeśli kod jest skompilowany dla architektury 64-bitowych, wartość wskaźnika (64-bitowy) zostaną obcięte Jeśli przypisano do `int` (32-bitowy). Aby uzyskać więcej informacji, zobacz [reguły dla wskaźników przy użyciu](http://msdn.microsoft.com/library/windows/desktop/aa384242).  
  
 Aby uzyskać dodatkowe informacje na temat typowych przyczyn ostrzeżenie C4311, zobacz [typowe błędy kompilatora](http://msdn.microsoft.com/library/windows/desktop/aa384160).  
  
 Poniższy przykład kodu generuje C4311 podczas kompilacji elementu docelowego 64-bitowe i pokazuje, jak to naprawić:  
  
```  
// C4311.cpp  
// compile by using: cl /W1 C4311.cpp  
int main() {  
   void* p = &p;  
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets  
   unsigned long long j = (unsigned long long) p;   // OK  
}  
  
```