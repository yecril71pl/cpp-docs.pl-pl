---
title: /Q Opcje (Operacje na niskim poziomie)
ms.date: 01/08/2020
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 9dd3675f200be4f0ec66620bcf3cf05706991b66
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518179"
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

- [/Qvec-Report (poziom raportowania automatycznej wektoryzator)](qvec-report-auto-vectorizer-reporting-level.md): włącza poziomy raportowania dla automatycznej wektoryzacji.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
