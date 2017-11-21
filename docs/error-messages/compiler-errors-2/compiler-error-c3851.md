---
title: "C3851 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3851
dev_langs: C++
helpviewer_keywords: C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ed2a62b859e37455041171c81bb6830db372c697
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3851"></a>C3851 błąd kompilatora
"char": universal-character-name nie może wyznaczyć znaku w podstawowym zestawie znaków  
  
 W kodzie skompilowanym jako C++ nie można użyć reprezentującą znak w zestawie znaków źródła podstawowa poza ciąg lub literał znakowy nazwa zawierająca znaki uniwersalne. Aby uzyskać więcej informacji, zobacz [zestawów znaków](../../cpp/character-sets2.md). W kodzie skompilowanym c, nie można użyć nazwa zawierająca znaki uniwersalne znaków w zakresie wartości 0x20 0x7f, włącznie z wyjątkiem 0x24 ('$'), 0x40 ("@"), lub 0x60 ("").  
  
 Poniższe przykłady Generowanie C3851 i pokazują, jak rozwiązywanie:  
  
```cpp  
// C3851.cpp  
int main()  
{  
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set  
   int test2_A = 0;        // OK  
}  
```