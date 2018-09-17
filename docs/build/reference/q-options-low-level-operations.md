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
ms.openlocfilehash: 15854333a9f26f87d20f7819327e68050ab37bf6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717791"
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
