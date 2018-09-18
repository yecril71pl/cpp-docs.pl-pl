---
title: Błąd kompilatora C2338 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2338
dev_langs:
- C++
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77bc98afdad36e0505abb58ee06ec1c7e7654ae5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071578"
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
