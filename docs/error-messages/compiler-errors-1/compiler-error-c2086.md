---
title: C2086 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2086
dev_langs:
- C++
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04f1a21c06adeeda5d9db428e984da51f06addb5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170258"
---
# <a name="compiler-error-c2086"></a>C2086 błąd kompilatora
"identyfikator": zmiana definicji  
  
 Identyfikator jest zdefiniowany więcej niż raz lub następującą po nim deklarację różni się od poprzedniego.  
  
 C2086 może być również wynik kompilowanie przyrostowej dla przywoływanego zestawu języka C#. Odbuduj zestawu języka C#, aby rozwiązać ten problem.  
  
 Poniższy przykład generuje C2086:  
  
```  
// C2086.cpp  
main() {  
  int a;  
  int a;   // C2086 not an error in ANSI C  
}  
```