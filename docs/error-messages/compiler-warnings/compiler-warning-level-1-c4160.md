---
title: "Kompilatora (poziom 1) ostrzeżenie C4160 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4160
dev_langs: C++
helpviewer_keywords: C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 129dfabde1cba003ab31b763c0a94386318c38a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4160"></a>Kompilator C4160 ostrzegawcze (poziom 1)
**#pragma**   
 ***pragma* (pop,...): nie znaleziono poprzednio włożonego identyfikatora "**   
 ***Identyfikator* "**  
  
 Instrukcję pragma w kodzie źródłowym próbuje pop identyfikator, który nie został przypisany. Aby uniknąć tego ostrzeżenia, należy poprawnie przypisany identyfikator są zdjęte ze stosu.  
  
 Poniższy przykład generuje C4160:  
  
```  
// C4160.cpp  
// compile with: /W1  
#pragma pack(push)  
  
#pragma pack(pop, id)   // C4160  
// use identifier when pushing to resolve the warning  
// #pragma pack(push, id)  
  
int main() {  
}  
```