---
title: "Kompilatora (poziom 1) ostrzeżenie C4716 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4716
dev_langs: C++
helpviewer_keywords: C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a1d9d1e91656e464a5af809f1559eddba5da3291
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4716"></a>Kompilator C4716 ostrzegawcze (poziom 1)
"function" musi zwracać wartość  
  
 Dana funkcja nie zwrócił wartość.  
  
 Tylko funkcje z zwracanego typu void może użyć polecenia zwracany bez towarzyszącego wartości zwracanej.  
  
 Niezdefiniowana wartość będą zwracane, gdy ta funkcja jest wywoływana.  
  
 To ostrzeżenie zostanie automatycznie podwyższony do wystąpił błąd. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md).  
  
 Poniższy przykład generuje C4716:  
  
```  
// C4716.cpp  
// compile with: /c /W1  
// C4716 expected  
#pragma warning(default:4716)  
int test() {  
   // uncomment the following line to resolve  
   // return 0;  
}  
```