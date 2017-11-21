---
title: "Kompilatora (poziom 3) ostrzeżenie C4645 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4645
dev_langs: C++
helpviewer_keywords: C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c327aa47f46ffa7d7533d818d5140fdc5a5933af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4645"></a>Kompilator C4645 ostrzegawcze (poziom 3)
Funkcja zadeklarowana ze __declspec(noreturn) zawiera instrukcję return  
  
 A [zwracać](../../cpp/return-statement-in-program-termination-cpp.md) instrukcji został znaleziony w funkcji, która jest oznaczony atrybutem [noreturn](../../cpp/noreturn.md) `__declspec` modyfikator. `return` Instrukcja została zignorowana.  
  
 Poniższy przykład generuje C4645:  
  
```  
// C4645.cpp  
// compile with:  /W3  
void __declspec(noreturn) func() {  
   return;   // C4645, delete this line to resolve  
}  
  
int main() {  
}  
```