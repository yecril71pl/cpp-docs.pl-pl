---
title: Błąd kompilatora C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 93b6e414f26c56702a1c7ac12863cbcd5063b570
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177498"
---
# <a name="compiler-error-c2558"></a>Błąd kompilatora C2558

'identifier' : nie ma dostępnego konstruktora kopiującego lub konstruktor kopiujący jest zadeklarowany jako 'explicit'

Konstruktor kopiujący inicjuje obiekt z innego obiektu tego samego typu. (Tworzy kopię obiektu). Kompilator generuje domyślny konstruktor kopiujący, jeśli nie zdefiniowano żadnych konstruktorów.

### <a name="to-fix-this-error"></a>Aby naprawić ten błąd

1. Problem może wystąpić, gdy podejmowana jest próba skopiowania klasy, której Konstruktor kopiujący jest `private`. W większości przypadków nie należy kopiować klasy, która ma Konstruktor kopiujący `private`. Wspólna technika programistyczna deklaruje Konstruktor kopiujący `private`, aby zapobiec bezpośredniemu użyciu klasy. Klasa może być bezużyteczna samodzielnie lub wymagać innej klasy, aby działać poprawnie.

   Jeśli określisz, że można bezpiecznie użyć klasy, która ma `private` Konstruktor kopiujący, Utwórz nową klasę z klasy, która ma Konstruktor `private` i Udostępnij `public` lub `protected` konstruktora kopiującego dostępnego w nowej klasie. Użyj klasy pochodnej zamiast oryginalnej.

1. Problem może wystąpić, gdy podejmowana jest próba skopiowania klasy, której Konstruktor kopiujący jest jawny. Deklarowanie konstruktora kopiującego jako `explicit` uniemożliwia przekazywanie/zwracanie obiektów klasy do/z funkcji. Aby uzyskać więcej informacji na temat jawnych konstruktorów, zobacz [konwersje typów zdefiniowane przez użytkownika](../../cpp/user-defined-type-conversions-cpp.md).

1. Problem może wystąpić, gdy podejmowana jest próba skopiowania wystąpienia klasy zadeklarowanego `const` przy użyciu konstruktora kopiującego, który nie przyjmuje `const` parametru odwołania. Zadeklaruj konstruktor kopiujący z odwołaniem typu `const`, a nie odwołaniem typu niestałego.
