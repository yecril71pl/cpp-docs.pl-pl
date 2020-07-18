---
title: Błąd narzędzi konsolidatora LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: cce2c03783039a62b5cb6f60ecf8d76b23589483
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446704"
---
# <a name="linker-tools-error-lnk1318"></a>Błąd narzędzi konsolidatora LNK1318

> Nieoczekiwany błąd PDB; *Przyczyna* "*szczegóły*"

Konsolidator napotkał nieoczekiwany błąd podczas otwierania, odczytywania lub zapisywania do pliku PDB.

Ten komunikat o błędzie jest generowany w przypadku nietypowych problemów w plikach PDB. *Przyczyna* i *szczegóły* przedstawiają informacje dostępne dla konsolidatora, gdy wystąpił błąd. Może to nie być bardzo przydatne, ponieważ typowe błędy podczas pracy z plikami PDB mają oddzielne, bardziej informacyjne komunikaty o błędach.

Ze względu na to, że Źródło błędu jest nietypowe, dostępne są tylko ogólne porady dotyczące rozwiązywania tego problemu:

- Wykonaj czystą operację w katalogach kompilacji, a następnie wykonaj pełną kompilację rozwiązania.

- Uruchom ponownie komputer lub Wyszukaj niedziałające lub nieodpowiadające procesy mspdbsrv.exe i Kasuj je w programie taskmanager.

- Wyłącz sprawdzanie oprogramowania antywirusowego w katalogach projektu.

- Użyj opcji kompilatora [/ZF](../../build/reference/zf.md) , jeśli używasz [/MP](../../build/reference/mp-build-with-multiple-processes.md) z MSBuild lub innego procesu kompilacji równoległej.

- Spróbuj skompilować, używając 64-bitowego hostowanego zestawu narzędzi.

- Serializacja łączenia do rozwiązywania problemów z łączem równoległym w razie potrzeby. Ten błąd może być spowodowany tym, że mspdbsrv.exe jest uruchamiana przez jedno wystąpienie linku i zostanie zamknięty przed użyciem innego wystąpienia linku. Minusem do tej poprawki polega na tym, że kompilacje projektu mogą trwać znacznie dłużej.
