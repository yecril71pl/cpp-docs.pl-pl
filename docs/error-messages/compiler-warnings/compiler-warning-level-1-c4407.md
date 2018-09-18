---
title: Kompilator ostrzeżenie (poziom 1) C4407 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a9a665dbb71157b37f72d3d0721357d00dc37230
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032606"
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