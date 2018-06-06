---
title: LNK1318 błąd narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1318
dev_langs:
- C++
helpviewer_keywords:
- LNK1318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 364c819c6ec2bf6e1195011eced6e6ad1699877b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570903"
---
# <a name="linker-tools-error-lnk1318"></a>LNK1318 błąd narzędzi konsolidatora

> Nieoczekiwany błąd w pliku PDB; *spowodować* "*szczegóły*"

Konsolidator napotkał nieoczekiwany błąd podczas otwierania, odczytywania lub zapisywania w pliku PDB.

Ten komunikat o błędzie jest generowany rzadko problemów z plików PDB. *Spowodować* i *szczegóły* stanowią informacje dostępne do konsolidatora, gdy wystąpił błąd. To może nie być bardzo przydatne, jako typowe błędy przy obsłudze PDB, pliki mają osobne komunikaty więcej informacji.

Ponieważ źródła błędu jest rzadko, Brak dostępnej tylko ogólne porady dotyczące rozwiązywania tego problemu:

- Wykonaj czystą operacji w katalogach kompilacji, a następnie wykonaj pełnej kompilacji rozwiązania.

- Ponowne uruchomienie komputera, lub sprawdź, czy mspdbsrv.exe stray lub zawieszone procesy i kasowanie je w Menedżer zadań.

- Wyłącz sprawdzanie oprogramowania antywirusowego w katalogach projektu.

- Użyj [/Zf](../../build/reference/zf.md) opcję kompilatora, jeśli przy użyciu [/MP](../../build/reference/mp-build-with-multiple-processes.md) MSBuild lub innego równoległych proces kompilacji.

- Spróbuj kompilowanie przy użyciu hostowaniem 64-bitowym.

- Serializować łączenie złagodzić łączenie równoległych zagadnień, w razie potrzeby. Ten błąd może być spowodowany mspdbsrv.exe jest uruchamiana przez jedno wystąpienie łącza i jest zamknięta, zanim inne wystąpienie łącza odbywa się za jego pomocą. Wadą interfejsu, aby ta poprawka jest, że kompilacji projektu może trwać znacznie dłużej, aby zakończyć.