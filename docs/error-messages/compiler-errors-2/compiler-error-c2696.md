---
title: Błąd kompilatora C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: f6af217dbcd871ac4edd1852042144802388545b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216092"
---
# <a name="compiler-error-c2696"></a>Błąd kompilatora C2696

Nie można utworzyć obiektu tymczasowego typu zarządzanego "Type".

Odwołania do **`const`** programu w niezarządzanym programie powodują wywołanie konstruktora przez kompilator i utworzenie obiektu tymczasowego na stosie. Jednak klasy zarządzanej nigdy nie można utworzyć na stosie.

C2696 jest osiągalna tylko przy użyciu przestarzałej opcji kompilatora **/CLR: oldSyntax**.
