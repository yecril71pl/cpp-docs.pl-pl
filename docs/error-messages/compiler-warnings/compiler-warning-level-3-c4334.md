---
title: "Kompilatora (poziom 3) ostrzeżenie C4334 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4334
dev_langs: C++
helpviewer_keywords: C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dba8fe25bc6401c0b823205bcc163dced466d4b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4334"></a>Kompilator C4334 ostrzegawcze (poziom 3)
"operator": wynik 32-bitowe przesunięcia niejawnie skonwertowano do 64 bitów (czy 64-bitowe przesunięcie było zamierzone?)  
  
 Wynik 32-bitowe przesunięcia niejawnie został przekonwertowany na 64-bitowej i podejrzewa kompilatora czy 64-bitowe przesunięcie było zamierzone.  Aby usunąć to ostrzeżenie, użyj 64-bitowe przesunięcie lub jawnie Rzutuj wynik przesunięcia do 64-bitowej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4334.  
  
```  
// C4334.cpp  
// compile with: /W3 /c  
void SetBit(unsigned __int64 *p, int i) {  
   *p |= (1 << i);   // C4334  
   *p |= (1i64 << i);   // OK  
}  
```