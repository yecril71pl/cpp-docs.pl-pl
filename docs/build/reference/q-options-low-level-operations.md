---
title: /Q Opcje (Operacje na niskim poziomie)
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: a6dcbd256fa3510955884d3adba4855b23cdbfab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514260"
---
# <a name="q-options-low-level-operations"></a>/Q Opcje (Operacje na niskim poziomie)

Możesz użyć **/q** opcje kompilatora, aby wykonywać następujące operacje kompilatora niskiego poziomu:

- [/ Qfast_transcendentals (Wymuszaj Fast Transcendentals)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): generuje fast transcendentals.

- [/ QIfist (pomijanie _ftol)](../../build/reference/qifist-suppress-ftol.md): pomija `_ftol` gdy konwersja typu zmiennoprzecinkowego na typ całkowitoliczbowy jest wymagana (tylko x86).

- [/ Qimprecise_fwaits (usuwanie fwaits wewnątrz bloków Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): usuwa `fwait` polecenia wewnątrz `try` bloków.

- [/ Qpar (automatyczny Paralelizator)](../../build/reference/qpar-auto-parallelizer.md): Włącza automatyczne przetwarzanie równoległe pętli, które są oznaczone [#pragma loop()](../../preprocessor/loop.md) dyrektywy.

- [/ Qpar raport (poziom raportowania automatycznej Paralelizacji)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): włącza poziomy raportowania dla automatycznego przetwarzania równoległego.

- [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): powoduje pominięcie optymalizacji zmiennoprzecinkowa rejestr ładuje i aby poruszać się między pamięcią i MMX rejestruje.

- [/ Qspectre](../../build/reference/qspectre.md): generuje instrukcje, aby uniknąć niektórych luk w zabezpieczeniach Spectre.

- [/ Qvec raport (poziom raportowania automatycznej Wektoryzacji)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): włącza poziomy raportowania dla automatycznej wektoryzacji.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
