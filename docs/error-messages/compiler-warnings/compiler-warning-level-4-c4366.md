---
title: "Kompilatora (poziom 4) ostrzeżenie C4366 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4366
dev_langs: C++
helpviewer_keywords: C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0d610bfcf2e432870fc081298d3dfc3a60c73bd4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4366"></a>Kompilator C4366 ostrzegawcze (poziom 4)
Wynik operatora jednoargumentowego "operator" może być niewyrównany  
  
 Jeśli na element członkowski struktury kiedykolwiek może być niewyrównany spowodowane pakowania, kompilator wyświetli ostrzeżenie, kiedy przypisano adres użytkownika wyrównany wskaźnika. Domyślnie wszystkie wskaźniki są wyrównane.  
  
 Aby rozwiązać C4366, zmienić wyrównania struktury lub zadeklarować wskaźnika z [__unaligned](../../cpp/unaligned.md) — słowo kluczowe.  
  
 Aby uzyskać więcej informacji, zobacz __unaligned i [pakietu](../../preprocessor/pack.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4366.  
  
```  
// C4366.cpp  
// compile with: /W4 /c  
// processor: IPF x64  
#pragma pack(1)  
struct X {  
   short s1;  
   int s2;  
};  
  
int main() {  
   X x;  
   short * ps1 = &x.s1;   // OK  
   int * ps2 = &x.s2;   // C4366  
}  
```