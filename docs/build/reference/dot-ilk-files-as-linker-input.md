---
title: Pliki .Ilk — Wejście konsolidatora
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 252c1cd6e17346954fce7ebf16134246da76ba57
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808472"
---
# <a name="ilk-files-as-linker-input"></a>Pliki .Ilk — Wejście konsolidatora

Gdy łączenie przyrostowe, łącze aktualizuje plik .ilk stanu, utworzony podczas pierwszego konsolidowania przyrostowego. Ten plik ma taką samą nazwę jak plik .exe lub pliku .dll i ma .ilk rozszerzenia. Podczas kolejne łącza przyrostowe łącze aktualizuje plik .ilk. Jeśli brakuje pliku .ilk LINK wykonuje pełne połączenie i tworzy nowy plik .ilk. Jeśli plik .ilk jest bezużyteczny, LINK wykonuje nieprzyrostowa łącza. Szczegółowe informacje na temat konsolidowania przyrostowego, zobacz [łącza przyrostowe (/ INCREMENTAL)](incremental-link-incrementally.md) opcji.

## <a name="see-also"></a>Zobacz także

[Pliki wejściowe LINK](link-input-files.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
