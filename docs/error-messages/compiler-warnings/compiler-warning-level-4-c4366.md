---
title: Kompilatora (poziom 4) ostrzeżenie C4366 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4366
dev_langs:
- C++
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12410a567cb55d6dea74b8e5e595009e56b1071f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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