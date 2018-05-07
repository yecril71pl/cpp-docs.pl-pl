---
title: Kompilatora (poziom 1) ostrzeżenie C4407 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4407
dev_langs:
- C++
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbc02c32463703f658cef1d5756926311d89b193
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4407"></a>Kompilator C4407 ostrzegawcze (poziom 1)
Rzutowanie pomiędzy innego wskaźnika do reprezentacji elementu członkowskiego, kompilator może wygenerować niepoprawny kod  
  
 Wykryto nieprawidłowe rzutowanie.  
  
 C4407 mogą być generowane z powodu pracy zgodność kompilatora, która została wykonana w programie Visual C++ 2005. Wskaźnik do elementu członkowskiego teraz wymaga nazwy kwalifikowanej i address-of — operator (&).  
  
 C4407 może wystąpić, jeśli rzutowanie między wieloma dziedziczenia wskaźnik do elementu członkowskiego na pojedyncze dziedziczenie wskaźnik do-elementu członkowskiego. Czasami może się powtórzy, ale czasami nie ponieważ reprezentacja wskaźnika do elementu członkowskiego pojedyncze dziedziczenie nie zawiera wystarczających informacji. Kompilowanie przy użyciu **/VMM** mogą ułatwić (Aby uzyskać więcej informacji, zobacz [/VMM, / VMS, / vmv (ogólna reprezentacja celu)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Można też spróbować zmienianie rozmieszczenia z klas podstawowych; Kompilator wykrywanie utratę danych podczas konwersji, ponieważ niezerowym przesunięciu z pochodnej klasy podstawowej.  
  
 Poniższy przykład generuje C4407:  
  
```  
// C4407.cpp  
// compile with: /W1 /c  
struct C1 {};  
struct C2 {};  
struct C3 : C1, C2 {};  
  
typedef void(C3::*PMF_C3)();  
typedef void(C2::*PMF_C2)();  
  
PMF_C2 f1(PMF_C3 pmf) {  
   return (PMF_C2)pmf;   // C4407, change type of cast,  
   // or reverse base class inheritance of C3 (i.e. : C2, C1)  
}  
```