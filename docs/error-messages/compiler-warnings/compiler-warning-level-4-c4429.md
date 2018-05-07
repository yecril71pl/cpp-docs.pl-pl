---
title: Kompilatora (poziom 4) ostrzeżenie C4429 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4429
dev_langs:
- C++
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00d4812fb1eefdd4364376288f063a6bf8b5dddf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4429"></a>Kompilator C4429 ostrzegawcze (poziom 4)
możliwa niekompletna lub nieprawidłowo sformułowana universal-character-name  
  
 Kompilator wykryto sekwencja znaków, które mogą być źle sformułowane Uniwersalna nazwa znaku. Nazwa zawierająca znaki uniwersalne jest `\u` następuje czterech cyfr szesnastkowych, lub `\U` następuje osiem znaków szesnastkowych.  
  
 Poniższy przykład generuje C4429:  
  
```  
// C4429.cpp  
// compile with: /W4 /WX  
int \ug0e4 = 0;   // C4429  
// Try the following line instead:  
// int \u00e4 = 0;   // OK, a well-formed universal character name.  
```