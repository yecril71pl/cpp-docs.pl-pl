---
title: Ustawianie opcji konsolidatora
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
ms.openlocfilehash: 5b885ad5c86bc59029fc6a3a60ccee385703ab2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508943"
---
# <a name="setting-linker-options"></a>Ustawianie opcji konsolidatora

Można ustawić opcje konsolidatora wewnątrz lub na zewnątrz środowiska programistycznego. Temat dla każdej opcji konsolidatora omówiono, jak je ustawić w środowisku programistycznym. Zobacz [opcje konsolidatora](../../build/reference/linker-options.md) pełną listę.

Po uruchomieniu łącze poza środowiskiem programistycznym, należy określić dane wejściowe w jeden lub więcej sposobów:

- Na [wiersza polecenia](../../build/reference/linker-command-line-syntax.md)

- Za pomocą [pliki poleceń](../../build/reference/link-command-files.md)

- W [zmiennych środowiskowych](../../build/reference/link-environment-variables.md)

Opcje procesów pierwszy LINK określone w zmiennej środowiskowej łącza, następuje opcje w kolejności są one określone w wierszu polecenia i w plikach poleceń. Jeśli opcja jest powtarzany z różnymi argumentami, pierwszeństwo ma ostatni przetworzony.

Opcje mają zastosowanie do całej kompilacji; Brak opcji można zastosować do określonych plików wejściowych.

## <a name="see-also"></a>Zobacz też

[Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)