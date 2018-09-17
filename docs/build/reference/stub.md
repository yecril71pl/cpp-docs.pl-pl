---
title: STUB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 151d7b425a7f397a05e3a06e9d94489a0c76f899
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725117"
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