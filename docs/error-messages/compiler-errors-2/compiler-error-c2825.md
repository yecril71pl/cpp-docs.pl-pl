---
title: "C2825 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2825
dev_langs: C++
helpviewer_keywords: C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ebe700fed581eadbab256c9c4f9e2f71bf1d1585
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2825"></a>C2825 błąd kompilatora
var: musi być klasą lub przestrzenią nazw, gdy następuje '::'  
  
 Nie powiodło się podjęto próbę utworzenia nazwy kwalifikowanej.  
  
 Na przykład, upewnij się, że kod nie zawiera deklaracji funkcji, w którym rozpoczyna się od nazwy funkcji::.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2825:  
  
```  
// C2825.cpp  
typedef int i;  
int main() {  
   int* p = new int;  
   p->i::i();   // C2825  
   // try the following line instead  
   // p->i::~i();  
}  
```