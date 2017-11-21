---
title: "Kompilatora (poziom 1) ostrzeżenie C4028 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4028
dev_langs: C++
helpviewer_keywords: C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0041d795ed5afce50592f21f41986d3f32c71fe3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4028"></a>Kompilator C4028 ostrzegawcze (poziom 1)
Parametr formalny "number" różni się od deklaracji  
  
 Typ parametrów formalnych nie zgadza się z odpowiadającym mu parametrem w deklaracji. Typ w oryginalnej deklaracji jest używany.  
  
 To ostrzeżenie jest prawidłowa tylko dla kodu źródłowego C.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4028.  
  
```  
// C4028.c  
// compile with: /W1 /Za  
void f(int , ...);  
void f(int i, int j) {}   // C4028  
  
void g(int , int);  
void g(int i, int j) {}   // OK  
  
int main() {}  
```