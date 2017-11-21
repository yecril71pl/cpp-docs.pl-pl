---
title: "Kompilatora (poziom 1) ostrzeżenie C4311 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4311
dev_langs: C++
helpviewer_keywords: C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 85a07ff4477d52a2c9b60978c9f4ba00c2127906
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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