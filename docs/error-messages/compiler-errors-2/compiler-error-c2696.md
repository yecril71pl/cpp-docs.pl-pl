---
title: Compiler Error C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367606"
---
# <a name="compiler-error-c2696"></a>Compiler Error C2696

Nie można utworzyć tymczasowego obiektu tego typu zarządzanego "type"

Odwołuje się do `const` niezarządzanego w programie, że kompilator wywołanie konstruktora i utworzyć tymczasowego obiektu na stosie. Jednak klasy zarządzanej nigdy nie mogą być tworzone na stosie.

C2696 jest dostępna, przy użyciu opcji kompilatora przestarzałe **: oldsyntax**.
