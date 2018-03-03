---
title: "Kompilatora (poziom 1) ostrzeżenie C4829 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4829
dev_langs:
- C++
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d662aaf24526320c0ced706534099d4c94a3c9f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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