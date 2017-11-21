---
title: "Kompilatora (poziom 4) ostrzeżenie C4629 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4629
dev_langs: C++
helpviewer_keywords: C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9192261b99437c52235b1afaeaeb4f2c98d19c67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4629"></a>Kompilator C4629 ostrzegawcze (poziom 4)
użyto dwuznaku, sekwencja znaków "dwuznaku" interpretowane jako tokenu "char" (Wstaw spację między dwoma znakami, jeśli to nie mają)  
  
 W obszarze [/Za](../../build/reference/za-ze-disable-language-extensions.md), w przypadku wykrycia dwuznaku wyświetla ostrzeżenie kompilatora.  
  
 Poniższy przykład generuje C4629:  
  
```  
// C4629.cpp  
// compile with: /Za /W4  
int main()  
<%   // C4629 <% digraph for {  
}  
```