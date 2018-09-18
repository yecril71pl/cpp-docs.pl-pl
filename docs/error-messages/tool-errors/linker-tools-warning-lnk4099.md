---
title: Ostrzeżenie LNK4099 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50bdceaba2e72312febec4819b96df334b5398c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026014"
---
# <a name="linker-tools-warning-lnk4099"></a>Ostrzeżenie LNK4099 narzędzi konsolidatora

Nie można odnaleźć pliku PDB "filename", "bibliotek/obiektów" lub "ścieżce;" skonsolidowany obiektu bez informacji debugowania

Konsolidator nie może odnaleźć pliku .pdb. Skopiuj go do katalogu, który zawiera `object/library`.

Aby znaleźć nazwę pliku .pdb, skojarzone z plikiem obiektu:

1. Wyodrębnij plik obiektu z biblioteki za pomocą [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**.

1. Sprawdź ścieżkę do pliku .pdb o **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.

Można również kompilacji z [/z7](../../build/reference/z7-zi-zi-debug-information-format.md), więc pliku pdb nie musi być używane, lub usuń [/DEBUG](../../build/reference/debug-generate-debug-info.md) opcji konsolidatora, jeśli nie masz pliki .pdb dla obiektów, jest tworzone połączenie.