---
title: Zalety wbudowanego asemblera
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
ms.openlocfilehash: ecf1598ec90a8600e1fa9aae565724c254dc11e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556744"
---
# <a name="advantages-of-inline-assembly"></a>Zalety wbudowanego asemblera

**Microsoft Specific**

Ponieważ wbudowanego asemblera nie wymaga osobny zestaw i kroki łącze, jest bardziej wygodne niż stosowania oddzielnego asemblera. Wbudowany kod asemblera, można użyć dowolnego języka C nazwy zmiennej lub funkcji, która znajduje się w zakresie, dzięki czemu można łatwo ją zintegrować z kodu C programu. Ponieważ kod zestawu mogą być mieszane wbudowanego w instrukcjach języka C lub C++, tworzyć zadania, które są uciążliwe lub wręcz niemożliwe w C lub C++.

Zastosowań wbudowanego asemblera obejmują:

- Pisanie funkcji w języku zestawu.

- Optymalizacja miejscu krytyczna szybkość sekcje kodu.

- Sterowniki urządzeń, dzięki czemu dostęp bezpośrednie sprzętu.

- Pisania kodu prologu i epilogu dla wywołań "naked".

Wbudowany zestaw jest narzędziem specjalnego przeznaczenia. Jeśli planujesz portu aplikacji na różnych komputerach, prawdopodobnie będziesz chciał umieść kod specyficzny dla komputera w oddzielny moduł. Ponieważ wbudowanego asemblera nie obsługuje wszystkich Microsoft Macro Assembler firmy (MASM) dyrektywy makr i danych, może okazać się bardziej wygodne służące MASM dla tych modułów.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>