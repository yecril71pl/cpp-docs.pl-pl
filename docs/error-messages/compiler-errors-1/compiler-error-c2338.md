---
title: Błąd kompilatora C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: c92a95b97cb4c57d3ad5cfbf8fe1d9980d5362cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221214"
---
# <a name="compiler-error-c2338"></a>Błąd kompilatora C2338

> *Komunikat o błędzie*

Ten błąd może być spowodowany **`static_assert`** błędem podczas kompilacji. Komunikat jest dostarczany przez **`static_assert`** parametry.

Ten komunikat o błędzie może być również generowany przez zewnętrznych dostawców do kompilatora. W większości przypadków te błędy są zgłaszane przez bibliotekę DLL dostawcy atrybutów, taką jak ATLPROV. Niektóre typowe formy tego komunikatu obejmują:

- "*Attribute*" — dostawca atrybutów ATL: błąd *komunikatu* o*numerze* ATL

- Nieprawidłowe użycie atrybutu "*Attribute*"

- "*użycie*": niepoprawny format atrybutu "Usage"

Te błędy są często nieodwracalne i mogą następować krytyczne błędy kompilatora.

Aby rozwiązać te problemy, Popraw użycie atrybutu. Na przykład w niektórych przypadkach parametry atrybutu muszą być zadeklarowane, aby można było ich używać. Jeśli zostanie podany numer błędu ATL, zapoznaj się z dokumentacją tego błędu, aby uzyskać bardziej szczegółowe informacje.
