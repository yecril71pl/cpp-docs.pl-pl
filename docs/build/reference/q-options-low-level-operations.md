---
title: /Q Opcje (Operacje na niskim poziomie)
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 5bbb63b4f437f8aefd5c84c1c1c4bd20bdb965cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319398"
---
# <a name="q-options-low-level-operations"></a>/Q Opcje (Operacje na niskim poziomie)

Możesz użyć **/q** opcje kompilatora, aby wykonywać następujące operacje kompilatora niskiego poziomu:

- [/ Qfast_transcendentals (Wymuszaj Fast Transcendentals)](qfast-transcendentals-force-fast-transcendentals.md): Generuje fast transcendentals.

- [/ QIfist (pomijanie _ftol)](qifist-suppress-ftol.md): Pomija `_ftol` gdy konwersja typu zmiennoprzecinkowego na typ całkowitoliczbowy jest wymagana (tylko x86).

- [/ Qimprecise_fwaits (usuwanie fwaits wewnątrz bloków Try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Usuwa `fwait` polecenia wewnątrz `try` bloków.

- [/ Qpar (automatyczny Paralelizator)](qpar-auto-parallelizer.md): Włącza automatyczne przetwarzanie równoległe pętli, które są oznaczone [#pragma loop()](../../preprocessor/loop.md) dyrektywy.

- [/ Qpar raport (raportowania automatycznej Paralelizacji poziom)](qpar-report-auto-parallelizer-reporting-level.md): Włącza poziomy raportowania dla automatycznego przetwarzania równoległego.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): Powoduje pominięcie optymalizacji obciążeń roboczych zmiennoprzecinkowa rejestr i aby poruszać się między pamięcią i MMX rejestrów.

- [/Qspectre](qspectre.md): Generuje instrukcje, aby uniknąć niektórych luk w zabezpieczeniach Spectre.

- [/ Qvec raport (Auto-poziom raportowania automatycznej Wektoryzacji)](qvec-report-auto-vectorizer-reporting-level.md): Włącza poziomy raportowania dla automatycznej wektoryzacji.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
