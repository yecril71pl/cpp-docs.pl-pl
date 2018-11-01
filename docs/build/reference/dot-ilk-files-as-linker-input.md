---
title: Pliki .Ilk — Wejście konsolidatora
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 012ca9aaa50ac2f8bb9d95ef77df5bb7127c5b79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595978"
---
# <a name="ilk-files-as-linker-input"></a>Pliki .Ilk — Wejście konsolidatora

Gdy łączenie przyrostowe, łącze aktualizuje plik .ilk stanu, utworzony podczas pierwszego konsolidowania przyrostowego. Ten plik ma taką samą nazwę jak plik .exe lub pliku .dll i ma .ilk rozszerzenia. Podczas kolejne łącza przyrostowe łącze aktualizuje plik .ilk. Jeśli brakuje pliku .ilk LINK wykonuje pełne połączenie i tworzy nowy plik .ilk. Jeśli plik .ilk jest bezużyteczny, LINK wykonuje nieprzyrostowa łącza. Szczegółowe informacje na temat konsolidowania przyrostowego, zobacz [łącza przyrostowe (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) opcji.

## <a name="see-also"></a>Zobacz też

[Pliki wejściowe LINK](../../build/reference/link-input-files.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)