---
title: Kompilatora (poziom 1) ostrzeżenie C4160 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4160
dev_langs:
- C++
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31c7c82ed4f79ce81abdfabb2b52968c2a481e97
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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