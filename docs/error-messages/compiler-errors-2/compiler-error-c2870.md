---
title: C2870 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2870
dev_langs:
- C++
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe9f47a96422493d6d731a18add8c23ff683f14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243492"
---
# <a name="compiler-error-c2870"></a>C2870 błąd kompilatora
"Nazwa": definicja przestrzeni nazw musi znajdować się w zakresie pliku albo natychmiast w innej definicji przestrzeni nazw  
  
 Definicja przestrzeni nazw `name` niepoprawnie. Przestrzenie nazw musi być zdefiniowana w zakresie pliku (poza wszystkie bloki i klasy) albo natychmiast w innej przestrzeni nazw.  
  
 Poniższy przykład generuje C2870:  
  
```  
// C2870.cpp  
// compile with: /c  
int main() {  
   namespace A { int i; };   // C2870  
}  
```