---
title: "C2480 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2480
dev_langs: C++
helpviewer_keywords: C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 06f6c536d5756a19e28df7060373512e3e883a41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2480"></a>C2480 błąd kompilatora
"identyfikator": "thread" jest prawidłowy tylko dla elementów danych statycznego obszaru  
  
 Nie można użyć `thread` atrybutu z automatycznej zmiennej, niestatyczny element członkowski danych, parametr funkcji lub deklaracji lub definicji funkcji.  
  
 Użyj `thread` atrybutu dla zmiennych globalnych, statyczne elementy członkowskie danych i statycznych zmiennych lokalnych tylko.  
  
 Poniższy przykład generuje C2480:  
  
```  
// C2480.cpp  
// compile with: /c  
__declspec( thread ) void func();   // C2480  
__declspec( thread ) static int i;   // OK  
```