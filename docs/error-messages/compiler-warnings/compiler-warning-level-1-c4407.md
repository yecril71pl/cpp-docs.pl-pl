---
title: "Kompilatora (poziom 1) ostrzeżenie C4407 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4407
dev_langs:
- C++
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 736b5f99115d6e2a39ee77005c7b3248ac191453
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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