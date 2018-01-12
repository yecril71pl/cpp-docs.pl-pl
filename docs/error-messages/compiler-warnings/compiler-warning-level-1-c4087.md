---
title: "Kompilatora (poziom 1) ostrzeżenie C4087 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4087
dev_langs: C++
helpviewer_keywords: C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ef21fc01fc6c756eb68f90bd58f9b18456e12fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4087"></a>Kompilator C4087 ostrzegawcze (poziom 1)
"Funkcja": deklaracja zawiera listę parametrów "void"  
  
 Deklaracja funkcji nie ma formalnych parametrów, ale wywołanie funkcji ma rzeczywistych parametrów. Dodatkowe parametry są przekazywane według konwencji wywołania funkcji.  
  
 To ostrzeżenie jest dla kompilatora C.  
  
## <a name="example"></a>Przykład  
  
```  
// C4087.c  
// compile with: /W1  
int f1( void ) {  
}  
  
int main() {  
   f1( 10 );   // C4087  
}  
```