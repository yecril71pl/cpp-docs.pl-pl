---
title: STUB
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: 5224fdaa2a03dc615c9e7e7bb7f7ba822a40807e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822122"
---
# <a name="stub"></a>STUB

W przypadku użycia w pliku definicji modułu, który tworzy sterownik urządzenia wirtualnego (VxD), można określić nazwę pliku, która zawiera strukturę IMAGE_DOS_HEADER (zdefiniowany w Windows NT. H) można używać w sterownik urządzenia wirtualnego (VxD), a nie nagłówek domyślny.

```
STUB:filename
```

## <a name="remarks"></a>Uwagi

Aby określić sposób równoważny *filename* z [/STUB](stub-ms-dos-stub-file-name.md) — opcja konsolidatora.

STUB jest prawidłowy w pliku definicji modułu tylko wtedy, gdy tworzenie VxD.

## <a name="see-also"></a>Zobacz także

[Zasady dla instrukcji definicji modułu](rules-for-module-definition-statements.md)
