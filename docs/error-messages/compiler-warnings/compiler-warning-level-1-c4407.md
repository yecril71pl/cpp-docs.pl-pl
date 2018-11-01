---
title: Kompilator ostrzeżenie (poziom 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 5142e3800f3ad716166a27e3b0407a40999b5746
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436832"
---
# <a name="compiler-warning-level-1-c4407"></a>Kompilator ostrzeżenie (poziom 1) C4407

Wykonuj rzutowania między różnych reprezentacjami wskaźników do składowej, kompilator może wygenerować niepoprawny kod

Wykryto nieprawidłowe rzutowanie.

C4407 mogą być generowane z powodu pracy zgodności kompilatora, która została wykonana w programie Visual C++ 2005. Wskaźnik do elementu członkowskiego, teraz wymaga kwalifikowana nazwa i operatora address-of (&).

C4407 może wystąpić, jeśli rzutowanie między wieloma dziedziczenia wskaźnika do składowej na pojedyncze dziedziczenie wskaźnika do składowej. Czasami może się powtórzy, ale czasami nie ponieważ reprezentacja wskaźnika do elementu członkowskiego pojedyncze dziedziczenie nie ma wystarczających informacji. Kompilowanie przy użyciu **/VMM** mogą pomóc (Aby uzyskać więcej informacji, zobacz [/VMM, / VMS, / vmv (ogólna reprezentacja celu)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Możesz też spróbować rozmieszczanie swojej klasy bazowej; Kompilator wykrywa utraty informacji w konwersji, ponieważ klasa bazowa jest przesunięciem od zera z pochodnej.

Poniższy przykład spowoduje wygenerowanie C4407:

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