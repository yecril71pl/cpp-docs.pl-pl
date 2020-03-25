---
title: Ostrzeżenie kompilatora (poziom 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: 76a33b24446debffb2c00bf1b0497cfc86022ce0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175145"
---
# <a name="compiler-warning-level-1-c4788"></a>Ostrzeżenie kompilatora (poziom 1) C4788

"Identyfikator": identyfikator został obcięty do znaków "number"

Kompilator ogranicza maksymalną długość dozwoloną dla nazwy funkcji. Gdy kompilator generuje funclets dla kodu EH/SEH, tworzy nazwę polecenie funclet przez zaczekanie na nazwę funkcji z tekstem, na przykład "__catch", "\__unwind" lub innym ciągiem.

Utworzona nazwa polecenie funclet może być zbyt długa i kompilator obcina ją i generuje C4788.

Aby usunąć to ostrzeżenie, skróć oryginalną nazwę funkcji. Jeśli funkcja jest funkcją lub C++ metodą szablonu, użyj elementu typedef dla części nazwy. Na przykład:

```cpp
C1<x, y, z<T>>::C2<a,b,c>::f
```

można zastąpić:

```cpp
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

To ostrzeżenie występuje tylko w kompilatorze x64.
