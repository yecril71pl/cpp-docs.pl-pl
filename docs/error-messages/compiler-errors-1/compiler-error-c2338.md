---
title: Błąd kompilatora C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: 4ca3feb2a71efa60229afdbf918109a5d5d59cad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539597"
---
# <a name="compiler-error-c2338"></a>Błąd kompilatora C2338

> *komunikat o błędzie*

Ten błąd może być spowodowany przez `static_assert` wystąpił błąd podczas kompilacji. Komunikat jest dostarczany przez `static_assert` parametrów.

Ten komunikat o błędzie mogą być też generowane przez zewnętrznych dostawców w kompilatorze. W większości przypadków te błędy są zgłaszane przez dostawcę atrybutu biblioteki DLL, takie jak ATLPROV. Niektóre typowe rodzaje tego komunikatu, obejmują:

> "*atrybut*" dostawca atrybutów Atl: Błąd biblioteki ATL*numer* *wiadomości*

> Nieprawidłowe użycie atrybutu "*atrybut*"

> "*użycia*": nieprawidłowy format atrybutu "użycie"

Te błędy są często nieodwracalny, a następuje błąd krytyczny kompilatora.

Aby rozwiązać te problemy, popraw użycie atrybutu. Na przykład w niektórych przypadkach parametry atrybutów musi być zadeklarowany przed ich użyciem. Jeśli zostanie podany numer błędu ATL, sprawdź w dokumentacji tego błędu, aby uzyskać bardziej szczegółowe informacje.
