---
title: "Kompilatora (poziom 1) ostrzeżenie C4829 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4829
dev_langs: C++
helpviewer_keywords: C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a7fe8de7fd47b16397972a054c18cd266f8c588
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4829"></a>Kompilator C4829 ostrzegawcze (poziom 1)
Prawdopodobnie niepoprawne parametry funkcji main. Należy wziąć pod uwagę "intmain (Platform::Array\<Platform::String ^ > ^ ARGV —)"  
  
 Określone funkcje, takie jak main, nie może przyjąć odwołanie parametrów typu. Podczas kompilacji powiedzie się, prawdopodobnie nie uruchomi się obraz wynikowy.  
  
 Poniższy przykład generuje C4829:  
  
```  
// C4829.cpp  
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp  
int main(Platform::String ^ s) {}   // C4829  
  
```