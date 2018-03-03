---
title: "Kompilatora (poziom 1) ostrzeżenie C4920 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4920
dev_langs:
- C++
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c87237f5ac2240cfd2063c58055d626b72285287
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4920"></a>Kompilator C4920 ostrzegawcze (poziom 1)
element członkowski elementu członkowskiego wyliczenia wyliczenia = wartość już występuje w elemencie enum wyliczenia jako element członkowski = wartość  
  
 Jeśli .tlb, który jest przekazywany do #import ma tego samego symbol zdefiniowany w co najmniej dwa typy wyliczeniowe, to ostrzeżenie wskazuje, że kolejne identyczne symbole są ignorowane i będzie komentarzach w pliku danych .tlh —.  
  
 Zakładając, że .tlb, który zawiera:  
  
```  
library MyLib  
{  
    typedef enum {  
        enumMember = 512  
    } AProblem;  
  
    typedef enum {  
        enumMember = 1024  
    } BProblem;  
};  
```  
  
 Poniższe przykłady generuje C4920,  
  
```  
// C4920.cpp  
// compile with: /W1  
#import "t4920.tlb"   // C4920  
  
int main() {  
}  
```