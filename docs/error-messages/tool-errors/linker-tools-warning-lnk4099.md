---
title: Ostrzeżenie LNK4099 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: dcf4d44c3a0b5b10035af763040c2912afc8c6f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442178"
---
# <a name="linker-tools-warning-lnk4099"></a>Ostrzeżenie LNK4099 narzędzi konsolidatora

Nie można odnaleźć pliku PDB "filename", "bibliotek/obiektów" lub "ścieżce;" skonsolidowany obiektu bez informacji debugowania

Konsolidator nie może odnaleźć pliku .pdb. Skopiuj go do katalogu, który zawiera `object/library`.

Aby znaleźć nazwę pliku .pdb, skojarzone z plikiem obiektu:

1. Wyodrębnij plik obiektu z biblioteki za pomocą [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**.

1. Sprawdź ścieżkę do pliku .pdb o **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.

Można również kompilacji z [/z7](../../build/reference/z7-zi-zi-debug-information-format.md), więc pliku pdb nie musi być używane, lub usuń [/DEBUG](../../build/reference/debug-generate-debug-info.md) opcji konsolidatora, jeśli nie masz pliki .pdb dla obiektów, jest tworzone połączenie.