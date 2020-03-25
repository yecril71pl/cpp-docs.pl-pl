---
title: Zalety wbudowanego asemblera
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
ms.openlocfilehash: 7e634f78eca753487cf122ac95df55828bb64625
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169659"
---
# <a name="advantages-of-inline-assembly"></a>Zalety wbudowanego asemblera

**Specyficzne dla firmy Microsoft**

Ponieważ wbudowany asembler nie wymaga oddzielnego zestawu i kroków łączy, jest bardziej wygodne niż oddzielny asembler. Wbudowany kod asemblera może używać dowolnej zmiennej języka C lub nazwy funkcji, która znajduje się w zakresie, dzięki czemu można łatwo zintegrować ją z kodem C programu. Ze względu na to, że kod zestawu może być C++ mieszany w wierszu c lub instrukcji, może wykonywać zadania, które są uciążliwe lub niemożliwe w języku c lub C++.

Użycie zestawu wbudowanego obejmuje:

- Pisanie funkcji w języku asemblera.

- Optymalizacja w poziomie — najważniejsze sekcje kodu.

- Umożliwienie bezpośredniego dostępu do sprzętu dla sterowników urządzeń.

- Pisanie kodu prologu i epilogu dla wywołań "owies".

Wbudowany zestaw jest narzędziem specjalnego przeznaczenia. Jeśli planujesz port aplikacji na różnych maszynach, prawdopodobnie chcesz umieścić kod specyficzny dla maszyny w osobnym module. Ponieważ wbudowany asembler nie obsługuje wszystkich dyrektyw i danych makr asemblera (MASM) firmy Microsoft, przydatne może okazać się użycie MASM dla takich modułów.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
