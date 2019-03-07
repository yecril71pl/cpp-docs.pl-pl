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
ms.openlocfilehash: 61f4ee8d02cda5b2cd270d7ef789bf58060e7fdf
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423173"
---
# <a name="setting-linker-options"></a>Ustawianie opcji konsolidatora

Można ustawić opcje konsolidatora wewnątrz lub na zewnątrz środowiska programistycznego. Temat dla każdej opcji konsolidatora omówiono, jak je ustawić w środowisku programistycznym. Zobacz [opcje konsolidatora](../../build/reference/linker-options.md) pełną listę.

Po uruchomieniu łącze poza środowiskiem programistycznym, należy określić dane wejściowe w jeden lub więcej sposobów:

- Na [wiersza polecenia](../../build/reference/linker-command-line-syntax.md)

- Za pomocą [pliki poleceń](../../build/reference/link-command-files.md)

- W [zmiennych środowiskowych](../../build/reference/link-environment-variables.md)

Opcje procesów pierwszy LINK określone w zmiennej środowiskowej łącza, następuje opcje w kolejności są one określone w wierszu polecenia i w plikach poleceń. Jeśli opcja jest powtarzany z różnymi argumentami, pierwszeństwo ma ostatni przetworzony.

Opcje mają zastosowanie do całej kompilacji; Brak opcji można zastosować do określonych plików wejściowych.

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
