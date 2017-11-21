---
title: "C3807 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3807
dev_langs: C++
helpviewer_keywords: C3807
ms.assetid: 7e2b0aab-8c61-4e71-b9c1-fcaeb6a1b5ea
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fc8e760d295cc0a4c2482449038ea09e89547425
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3807"></a>C3807 błąd kompilatora
'type': klasa z atrybutem ComImport nie może pochodzić od "type2", tylko implementacja interfejsu jest dozwolona  
  
 Typ pochodny <xref:System.Runtime.InteropServices.ComImportAttribute> można tylko zaimplementować interfejs.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3807.  
  
```  
// C3807.cpp  
// compile with: /clr /c  
ref struct S {};  
interface struct I {};  
  
[System::Runtime::InteropServices::ComImportAttribute()]  
ref struct S1 : S {};   // C3807  
ref struct S2 : I {};  
```