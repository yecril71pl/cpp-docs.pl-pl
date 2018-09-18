---
title: Błąd kompilatora C2011 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2011
dev_langs:
- C++
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09946a6a3e974293e65a582c735e3de42503f0c3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115044"
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