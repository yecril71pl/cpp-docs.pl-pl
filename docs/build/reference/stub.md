---
title: STUB
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: 95f8e1584bdd87f23e87c27418c0debca5c3181a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533721"
---
# <a name="stub"></a>STUB

W przypadku użycia w pliku definicji modułu, który tworzy sterownik urządzenia wirtualnego (VxD), można określić nazwę pliku, która zawiera strukturę IMAGE_DOS_HEADER (zdefiniowany w Windows NT. H) można używać w sterownik urządzenia wirtualnego (VxD), a nie nagłówek domyślny.

```
STUB:filename
```

## <a name="remarks"></a>Uwagi

Aby określić sposób równoważny *filename* z [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) — opcja konsolidatora.

STUB jest prawidłowy w pliku definicji modułu tylko wtedy, gdy tworzenie VxD.

## <a name="see-also"></a>Zobacz też

[Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)