---
title: Pliki .Ilk — Wejście konsolidatora
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 6c0eb5627d7dd1b414351dc65685c0c5071d249e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422510"
---
# <a name="ilk-files-as-linker-input"></a>Pliki .Ilk — Wejście konsolidatora

Gdy łączenie przyrostowe, łącze aktualizuje plik .ilk stanu, utworzony podczas pierwszego konsolidowania przyrostowego. Ten plik ma taką samą nazwę jak plik .exe lub pliku .dll i ma .ilk rozszerzenia. Podczas kolejne łącza przyrostowe łącze aktualizuje plik .ilk. Jeśli brakuje pliku .ilk LINK wykonuje pełne połączenie i tworzy nowy plik .ilk. Jeśli plik .ilk jest bezużyteczny, LINK wykonuje nieprzyrostowa łącza. Szczegółowe informacje na temat konsolidowania przyrostowego, zobacz [łącza przyrostowe (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) opcji.

## <a name="see-also"></a>Zobacz także

[Pliki wejściowe LINK](../../build/reference/link-input-files.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
