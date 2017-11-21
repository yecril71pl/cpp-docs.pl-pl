---
title: "Kompilatora (poziom 4) ostrzeżenie C4429 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4429
dev_langs: C++
helpviewer_keywords: C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4a8d8a5454a02c3401f7e86645f2042715c0e11f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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