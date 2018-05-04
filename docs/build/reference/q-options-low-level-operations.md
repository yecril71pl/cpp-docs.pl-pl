---
title: -Q opcje (operacje na niskim poziomie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /q
dev_langs:
- C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a18c5d790cf21e8eb130a2b2baa152e20d79a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="q-options-low-level-operations"></a>/Q Opcje (Operacje na niskim poziomie)

Można użyć **/Q** opcji kompilatora, aby wykonywać następujące operacje kompilatora niskiego poziomu:

- [/ Qfast_transcendentals (Wymuszaj Fast Transcendentals)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): generuje fast transcendentals.

- [/ QIfist (pomijanie _ftol)](../../build/reference/qifist-suppress-ftol.md): pomija `_ftol` podczas konwersji z typu zmiennoprzecinkowego do typu Liczba całkowita jest wymagana (tylko x86).

- [/ Qimprecise_fwaits (usuwanie fwaits wewnątrz bloków Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): usuwa `fwait` poleceniach wewnątrz `try` bloków.

- [/ Qpar (automatyczny Paralelizator)](../../build/reference/qpar-auto-parallelizer.md): włącza automatyczna paralelizacja pętli, które są oznaczone ikoną z [#pragma loop()](../../preprocessor/loop.md) dyrektywy.

- [/ Qpar raport (poziom raportowania automatycznej Paralelizacji)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): Włącza raportowanie poziomy automatyczna paralelizacja.

- [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): powoduje pominięcie optymalizacji liczb zmiennoprzecinkowych rejestru ładuje i dla ruchu między pamięcią i MMX rejestruje.

- [/ Qspectre](../../build/reference/qspectre.md): generuje instrukcje, aby ograniczyć niektórych Spectre luk w zabezpieczeniach.

- [/ Qvec raport (poziom raportowania automatycznej Wektoryzacji)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): Włącza raportowanie poziomy vectorization automatycznego.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
