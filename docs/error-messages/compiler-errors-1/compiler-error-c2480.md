---
title: C2480 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2480
dev_langs:
- C++
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 987cefa42b3f3f8d9588e446ca181c0b7cd48f8c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198589"
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