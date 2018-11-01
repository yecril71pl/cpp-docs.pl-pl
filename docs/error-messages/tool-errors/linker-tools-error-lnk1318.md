---
title: LNK1318 błąd narzędzi konsolidatora
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: 8ed6489a27d4c0e117f7f18281ff188f40936e0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648737"
---
# <a name="linker-tools-error-lnk1318"></a>LNK1318 błąd narzędzi konsolidatora

> Nieoczekiwany błąd w pliku PDB; *spowodować* "*szczegóły*"

Konsolidator napotkał nieoczekiwany błąd podczas otwierania, odczytywania lub zapisywania w pliku PDB.

Ten komunikat o błędzie jest generowany dla nietypowe problemy z plików PDB. *Spowodować* i *szczegóły* stanowią informacje dostępne do konsolidatora, gdy wystąpił błąd. To może nie być bardzo przydatne jako typowych błędów, gdy komunikaty o błędach w oddzielnych, większą przyjazność dla radzenia sobie z plików PDB.

Ponieważ źródła błędu jest mało prawdopodobna, Brak dostępnej tylko ogólne porady dotyczące rozwiązywania tego problemu:

- Wykonania operacji czyszczenia w katalogach kompilacji, a następnie wykonaj pełny kompilacji rozwiązania.

- Ponowne uruchomienie komputera, lub sprawdź, czy mspdbsrv.exe zabłąkany lub zawieszone procesy i kill je w Menedżer zadań.

- Wyłącz sprawdzanie oprogramowania antywirusowego w katalogach projektu.

- Użyj [/Zf](../../build/reference/zf.md) opcji kompilatora, jeśli za pomocą [/MP](../../build/reference/mp-build-with-multiple-processes.md) przy użyciu programu MSBuild lub innego równoległe procesu kompilacji.

- Spróbować utworzyć za pomocą narzędzi z hostowaniem 64-bitowych.

- Serializuje łączenie ograniczyć równoległe łącze problemy, jeśli to konieczne. Ten błąd może być spowodowany mspdbsrv.exe jest uruchamiany przez jedno wystąpienie łącza i jest zamknięta, zanim inne wystąpienie łącza odbywa się za jej pomocą. Wadą, aby ta poprawka jest, że kompilacje projektu może zająć wyraźnie dłuższy.