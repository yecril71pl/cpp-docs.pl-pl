---
title: "Kompilatora (poziom 3) ostrzeżenie C4390 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4390
dev_langs: C++
helpviewer_keywords: C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 62e7573be5a3410075d2b7b5eed9c618be993859
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4390"></a>Kompilator C4390 ostrzegawcze (poziom 3)
";": pusta kontrolowane instrukcji znalezionej; jest to zamierzone?  
  
 Po instrukcji sterowania, który nie zawiera instrukcji znaleziono średnikiem.  
  
 Jeśli otrzymasz C4390 z powodu makra, należy użyć [ostrzeżenie](../../preprocessor/warning.md) pragma, aby wyłączyć C4390 w module zawierający makro.  
  
 Poniższy przykład generuje C4390:  
  
```  
// C4390.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
   if (i);   // C4390  
      i++;  
}  
```