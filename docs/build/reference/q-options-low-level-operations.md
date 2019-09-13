---
title: /Q Opcje (Operacje na niskim poziomie)
ms.date: 01/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 6348226aa38d1f2eefdf9e19e27c4c87bd2f0812
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927672"
---
# <a name="q-options-low-level-operations"></a>/Q Opcje (Operacje na niskim poziomie)

Można użyć **/q** opcji kompilatora, aby wykonać następujące operacje kompilatora niskiego poziomu:

- [/Qfast_transcendentals (Wymuś szybkie transcendentals)](qfast-transcendentals-force-fast-transcendentals.md): Generuje szybki transcendentals.

- [/QIfist (Pomijanie _ftol)](qifist-suppress-ftol.md): Pomija, `_ftol` gdy wymagana jest konwersja typu zmiennoprzecinkowego na typ Integer (tylko x86).

- [/Qimprecise_fwaits (usuwanie fwaits wewnątrz bloków try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Usuwa `fwait` polecenia wewnątrz `try` bloków.

- [/Qpar (autoparalelizacji)](qpar-auto-parallelizer.md): Włącza automatyczne przetwarzanie równoległe pętle, które są oznaczone za pomocą dyrektywy [pętli #pragma ()](../../preprocessor/loop.md) .

- [/Qpar-report (poziom raportowania autoparalelizacji)](qpar-report-auto-parallelizer-reporting-level.md): Włącza poziomy raportowania dla automatycznej przetwarzanie równoległe.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): Pomija optymalizacje w przypadku ładowania rejestru zmiennoprzecinkowego i przenoszenia między pamięcią a rejestrem MMX.

- [/Qspectre](qspectre.md): Generuje instrukcje w celu ograniczenia niektórych luk w zabezpieczeniach Spectre.

- [/Qvec-Report (poziom raportowania autowektoryzator)](qvec-report-auto-vectorizer-reporting-level.md): Włącza poziomy raportowania dla automatycznej wektoryzacji.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
