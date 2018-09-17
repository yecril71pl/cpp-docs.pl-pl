---
title: . Ilk, pliki jako dane wejściowe konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3b8de3758daf59a543cdcc9f3b73e1d6c6f0ce8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720593"
---
# <a name="ilk-files-as-linker-input"></a>Pliki .Ilk — Wejście konsolidatora

Gdy łączenie przyrostowe, łącze aktualizuje plik .ilk stanu, utworzony podczas pierwszego konsolidowania przyrostowego. Ten plik ma taką samą nazwę jak plik .exe lub pliku .dll i ma .ilk rozszerzenia. Podczas kolejne łącza przyrostowe łącze aktualizuje plik .ilk. Jeśli brakuje pliku .ilk LINK wykonuje pełne połączenie i tworzy nowy plik .ilk. Jeśli plik .ilk jest bezużyteczny, LINK wykonuje nieprzyrostowa łącza. Szczegółowe informacje na temat konsolidowania przyrostowego, zobacz [łącza przyrostowe (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) opcji.

## <a name="see-also"></a>Zobacz też

[Pliki wejściowe LINK](../../build/reference/link-input-files.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)