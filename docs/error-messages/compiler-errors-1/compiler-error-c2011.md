---
title: Błąd kompilatora C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: 14969c9cdf4b00844d2001bf4817ea7ffc9bfba6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361558"
---
# <a name="compiler-error-c2011"></a>Błąd kompilatora C2011

'Identyfikator': "type" wpisz ponownie definicję

Identyfikator został już zdefiniowany jako `type`. Sprawdź, czy definicji(-e) klas identyfikatora.

Możesz również uzyskać C2011 Jeśli importujesz plik nagłówkowy lub wpisz biblioteki więcej niż jeden raz w tym samym pliku. Zapobieganie wielu dołączeniom typów zdefiniowanych w pliku nagłówkowym, użyj obejmują osłony lub `#pragma` [po](../../preprocessor/once.md) dyrektywy w pliku nagłówkowym.

Jeśli musisz znaleźć początkowej deklaracji typu zmieniony, możesz użyć [/P](../../build/reference/p-preprocess-to-a-file.md) flagi kompilatora do generowania wstępnie przetworzone produkty wyjściowe są przekazywane do kompilator. Można użyć narzędzia wyszukiwania tekstu można znaleźć wystąpienia zmieniony identyfikatora w pliku wyjściowym.

Poniższy przykład generuje C2011 i pokazano jeden ze sposobów, aby rozwiązać ten problem:

```
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```