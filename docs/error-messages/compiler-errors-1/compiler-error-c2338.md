---
title: Błąd kompilatora C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: 2a76ecaf78b117b0c1acabd9fcd50c9ae0f73b98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188299"
---
# <a name="compiler-error-c2338"></a>Błąd kompilatora C2338

> *komunikat o błędzie*

Ten błąd może być spowodowany przez `static_assert` wystąpił błąd podczas kompilacji. Komunikat jest dostarczany przez `static_assert` parametrów.

Ten komunikat o błędzie mogą być też generowane przez zewnętrznych dostawców w kompilatorze. W większości przypadków te błędy są zgłaszane przez dostawcę atrybutu biblioteki DLL, takie jak ATLPROV. Niektóre typowe rodzaje tego komunikatu, obejmują:

- "*atrybut*" dostawca atrybutów Atl: Błąd biblioteki ATL*numer* *wiadomości*

- Nieprawidłowe użycie atrybutu "*atrybut*"

- "*użycia*": nieprawidłowy format atrybutu "użycie"

Te błędy są często nieodwracalny, a następuje błąd krytyczny kompilatora.

Aby rozwiązać te problemy, popraw użycie atrybutu. Na przykład w niektórych przypadkach parametry atrybutów musi być zadeklarowany przed ich użyciem. Jeśli zostanie podany numer błędu ATL, sprawdź w dokumentacji tego błędu, aby uzyskać bardziej szczegółowe informacje.
