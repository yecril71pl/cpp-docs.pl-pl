---
title: Błąd kompilatora C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 2504b42f49ccb040f676f0aead8f243d33c7dd1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207748"
---
# <a name="compiler-error-c2558"></a>Błąd kompilatora C2558

'identifier' : nie ma dostępnego konstruktora kopiującego lub konstruktor kopiujący jest zadeklarowany jako 'explicit'

Konstruktor kopiujący inicjuje obiekt z innego obiektu tego samego typu. (Tworzy kopię obiektu). Kompilator generuje domyślny konstruktor kopiujący, jeśli nie zdefiniowano żadnych konstruktorów.

### <a name="to-fix-this-error"></a>Aby naprawić ten błąd

1. Problem może wystąpić, gdy podejmowana jest próba skopiowania klasy, której Konstruktor kopiujący jest **`private`** . W większości przypadków Klasa, która ma **`private`** Konstruktor kopiujący, nie powinna być kopiowana. Wspólna technika programowania deklaruje **`private`** Konstruktor kopiujący, aby zapobiec bezpośredniemu użyciu klasy. Klasa może być bezużyteczna samodzielnie lub wymagać innej klasy, aby działać poprawnie.

   Jeśli określisz, że można bezpiecznie użyć klasy, która ma **`private`** Konstruktor kopiujący, Utwórz nową klasę z klasy, która ma **`private`** konstruktora i Udostępnij **`public`** **`protected`** Konstruktor kopiujący w nowej klasie. Użyj klasy pochodnej zamiast oryginalnej.

1. Problem może wystąpić, gdy podejmowana jest próba skopiowania klasy, której Konstruktor kopiujący jest jawny. Deklarowanie konstruktora kopiującego **`explicit`** uniemożliwia przekazywanie/zwracanie obiektów klasy do/z funkcji. Aby uzyskać więcej informacji na temat jawnych konstruktorów, zobacz [konwersje typów zdefiniowane przez użytkownika](../../cpp/user-defined-type-conversions-cpp.md).

1. Problem może wystąpić, gdy podejmowana jest próba skopiowania wystąpienia klasy zadeklarowanego **`const`** za pomocą konstruktora kopiującego, który nie przyjmuje **`const`** parametru odwołania. Zadeklaruj konstruktor kopiujący z **`const`** odwołaniem do typu, a nie odwołaniem typu niestałego.
