---
title: Błąd narzędzi konsolidatora LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: a61c11a9cbb25fea6fddc0bf1c5c4c2a7af1cf4f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183582"
---
# <a name="linker-tools-error-lnk1318"></a>Błąd narzędzi konsolidatora LNK1318

> Nieoczekiwany błąd PDB; *Przyczyna* "*szczegóły*"

Konsolidator napotkał nieoczekiwany błąd podczas otwierania, odczytywania lub zapisywania do pliku PDB.

Ten komunikat o błędzie jest generowany w przypadku nietypowych problemów w plikach PDB. *Przyczyna* i *szczegóły* przedstawiają informacje dostępne dla konsolidatora, gdy wystąpił błąd. Może to nie być bardzo przydatne, ponieważ typowe błędy podczas pracy z plikami PDB mają oddzielne, bardziej informacyjne komunikaty o błędach.

Ze względu na to, że Źródło błędu jest nietypowe, dostępne są tylko ogólne porady dotyczące rozwiązywania tego problemu:

- Wykonaj czystą operację w katalogach kompilacji, a następnie wykonaj pełną kompilację rozwiązania.

- Uruchom ponownie komputer lub sprawdź, czy są to procesy niewidoczne lub zawieszone w mspdbsrv. exe i Kasuj je w programie taskmanager.

- Wyłącz sprawdzanie oprogramowania antywirusowego w katalogach projektu.

- Użyj opcji kompilatora [/ZF](../../build/reference/zf.md) , jeśli używasz [/MP](../../build/reference/mp-build-with-multiple-processes.md) z MSBuild lub innego procesu kompilacji równoległej.

- Spróbuj skompilować, używając 64-bitowego hostowanego zestawu narzędzi.

- Serializacja łączenia do rozwiązywania problemów z łączem równoległym w razie potrzeby. Ten błąd może być spowodowany tym, że program mspdbsrv. exe jest uruchamiany przez jedno wystąpienie linku i jest zamykany przed użyciem innego wystąpienia linku. Minusem do tej poprawki polega na tym, że kompilacje projektu mogą trwać znacznie dłużej.
