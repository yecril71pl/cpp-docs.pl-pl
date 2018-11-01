---
title: C2558 błąd kompilatora
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: b0dca0b19d427cf83238c824739d288a1cfd54d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571733"
---
# <a name="compiler-error-c2558"></a>C2558 błąd kompilatora

'identifier' : nie ma dostępnego konstruktora kopiującego lub konstruktor kopiujący jest zadeklarowany jako 'explicit'

Konstruktor kopiujący inicjuje obiekt z innego obiektu tego samego typu. (Tworzy kopię obiektu.) Kompilator generuje domyślny konstruktor kopiujący, jeżeli nie zdefiniujesz żadnych konstruktorów.

### <a name="to-fix-this-error"></a>Aby naprawić ten błąd

1. Ten problem może wystąpić, gdy podejmowana jest próba skopiowania klasy, której Konstruktor kopiujący jest `private`. W większości przypadków klasy, która ma `private` konstruktora kopiującego nie powinny zostać skopiowane. Powszechnie stosowana technika programowania deklaruje `private` Konstruktor Kopiuj, aby zapobiegać bezpośredniemu wykorzystaniu klasy. Klasa może być bezużyteczna samodzielnie lub wymagać innej klasy, aby działać poprawnie.

   Jeśli stwierdzisz, że jest bezpieczne użycie klasy, która ma `private` Konstruktor kopiujący, pochodzi z nową klasę z klasy, która ma `private` marki i Konstruktor `public` lub `protected` Konstruktor kopiujący jest dostępna w nowej klasie. Użyj klasy pochodnej zamiast oryginalnej.

1. Ten problem może wystąpić, gdy podejmowana jest próba skopiowania klasy, której Konstruktor kopiujący jest jawny. Zadeklarowanie konstruktora kopiującego jako `explicit` zapobiega przekazywaniu/zwracaniu obiektów klasy do/z funkcji. Aby uzyskać więcej informacji dotyczących jawnych konstruktorów, zobacz [konwersje typów zdefiniowane przez użytkownika](../../cpp/user-defined-type-conversions-cpp.md).

1. Ten problem może wystąpić, gdy podejmowana jest próba skopiowania wystąpienia klasy zadeklarowane `const` za pomocą konstruktora kopiującego, który nie przyjmuje `const` odwołać się do parametru. Zadeklaruj Konstruktor kopiujący z `const` zamiast odwołania typu non-const.