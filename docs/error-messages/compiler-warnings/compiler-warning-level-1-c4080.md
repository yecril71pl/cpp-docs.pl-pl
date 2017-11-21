---
title: "Kompilatora (poziom 1) ostrzeżenie C4080 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4080
dev_langs: C++
helpviewer_keywords: C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 187456a528df6613bdcb8d919b7cb069b81b7a67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4080"></a>Kompilator C4080 ostrzegawcze (poziom 1)
Oczekiwano identyfikatora dla nazwy segmentu; Znaleziono symbol  
  
 Nazwa segmentu w [#pragma alloc_text](../../preprocessor/alloc-text.md) musi być ciągiem lub identyfikator. Kompilator ignoruje pragma, jeśli nie można odnaleźć prawidłowego identyfikatora.  
  
 Poniższy przykład generuje C4080:  
  
```  
// C4080.cpp  
// compile with: /W1  
extern "C" void func(void);  
  
#pragma alloc_text()   // C4080  
  
// try this line to resolve the warning  
// #pragma alloc_text("mysection", func)  
  
int main() {  
}  
  
void func(void) {  
}  
```