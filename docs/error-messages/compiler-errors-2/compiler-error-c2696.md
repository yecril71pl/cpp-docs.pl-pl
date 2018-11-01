---
title: Błąd kompilatora C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562878"
---
# <a name="compiler-error-c2696"></a>Błąd kompilatora C2696

Nie można utworzyć tymczasowego obiektu tego typu zarządzanego "type"

Odwołuje się do `const` niezarządzanego w programie, że kompilator wywołanie konstruktora i utworzyć tymczasowego obiektu na stosie. Jednak klasy zarządzanej nigdy nie mogą być tworzone na stosie.

C2696 jest dostępna, przy użyciu opcji kompilatora przestarzałe **: oldsyntax**.
