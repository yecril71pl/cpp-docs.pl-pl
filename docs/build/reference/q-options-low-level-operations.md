---
title: /Q Opcje (Operacje na niskim poziomie)
ms.date: 01/08/2020
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 722a63a43e5e08fe80b26f908c7ae92df2fdb29c
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034522"
---
# <a name="q-options-low-level-operations"></a>/Q Opcje (Operacje na niskim poziomie)

Można użyć **/q** opcji kompilatora, aby wykonać następujące operacje kompilatora niskiego poziomu:

- [/Qfast_transcendentals (Wymuś szybkie transcendentals)](qfast-transcendentals-force-fast-transcendentals.md): generuje szybkie transcendentals.

- [/QIfist (pomijaj _ftol)](qifist-suppress-ftol.md): pomija `_ftol`, gdy wymagana jest konwersja z typu zmiennoprzecinkowego na typ Integer (tylko x86).

- [/Qimprecise_fwaits (Usuń fwaits wewnątrz bloków try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): usuwa `fwait` polecenia wewnątrz bloków `try`.

- [/QIntel-JCC-Erratum](qintel-jcc-erratum.md): zmniejsza wpływ na wydajność spowodowany przez aktualizację sprawdzenia erraty włączenia MIKROKODU (JCC) firmy Intel.

- [/Qpar (automatyczne paralelizacji)](qpar-auto-parallelizer.md): włącza automatyczne przetwarzanie równoległe pętli, które są oznaczone za pomocą dyrektywy [#pragma loop ()](../../preprocessor/loop.md) .

- [/Qpar-report (poziom raportowania automatycznej paralelizacji)](qpar-report-auto-parallelizer-reporting-level.md): włącza poziomy raportowania dla automatycznej przetwarzanie równoległe.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): Pomija optymalizacje dla ładunków zmiennoprzecinkowych i umożliwia przenoszenie między pamięcią a rejestrem MMX.

- [/Qspectre](qspectre.md): generuje instrukcje w celu ograniczenia niektórych luk w zabezpieczeniach Spectre.

- [/Qspectre-Load](qspectre-load.md): generuje instrukcje w celu ograniczenia Spectre luk w zabezpieczeniach opartych na ładowaniu.

- [/Qspectre-Load-CF](qspectre-load-cf.md): generuje instrukcje w celu ograniczenia Spectre luk w zabezpieczeniach na podstawie instrukcji przepływu sterowania, które ładują.

- [/Qvec-Report (poziom raportowania automatycznej wektoryzator)](qvec-report-auto-vectorizer-reporting-level.md): włącza poziomy raportowania dla automatycznej wektoryzacji.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
