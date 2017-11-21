---
title: "C2190 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2190
dev_langs: C++
helpviewer_keywords: C2190
ms.assetid: 34e15f85-d979-4948-80fc-46c414508a70
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d004d5a80e6907695f742faf6573c348662a479b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2190"></a>C2190 błąd kompilatora
Pierwsza lista parametrów dłuższa niż druga  
  
 Funkcja C zadeklarowano z listą parametrów krótszą po raz drugi. C nie obsługuje funkcji przeciążenia.  
  
 Poniższy przykład generuje C2190:  
  
```  
// C2190.c  
// compile with: /Za /c  
void func( int, float );  
void func( int  );   // C2190, different parameter list  
void func2( int  );   // OK  
```