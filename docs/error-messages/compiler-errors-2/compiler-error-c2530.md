---
title: C2530 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b226ef5ca0e839c745e13d4118264a69ca408db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229405"
---
# <a name="compiler-error-c2530"></a>C2530 błąd kompilatora
'Identyfikator': odwołania muszą być zainicjowane  
  
 Należy zainicjować odwołanie podczas zostało zadeklarowane, o ile nie jest już zadeklarowany:  
  
-   Ze słowem kluczowym [extern](../../cpp/using-extern-to-specify-linkage.md).  
  
-   Jako element członkowski klasy, struktury lub związku (i została zainicjowana w konstruktorze).  
  
-   Jako parametru w deklaracji lub definicji funkcji.  
  
-   Jako typ zwracany funkcji.  
  
 Poniższy przykład generuje C2530:  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```