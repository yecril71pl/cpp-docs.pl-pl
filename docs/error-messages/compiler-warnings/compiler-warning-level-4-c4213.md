---
title: "Kompilatora (poziom 4) ostrzeżenie C4213 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4213
dev_langs: C++
helpviewer_keywords: C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 385397f186d87c96c956756e036023bc4085352b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4213"></a>Kompilator C4213 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: rzutowanie na l wartość  
  
 Rozszerzenia Microsoft domyślne (/Ze) można użyć rzutowania po lewej stronie instrukcji przypisania.  
  
## <a name="example"></a>Przykład  
  
```  
// C4213.c  
// compile with: /W4  
void *a;  
void f()  
{  
   int   i[3];  
   a = &i;  
   *(( int * )a )++ = 3;  // C4213  
}  
  
int main()  
{  
}  
```  
  
 Takie rzutowania są nieprawidłowe w obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).