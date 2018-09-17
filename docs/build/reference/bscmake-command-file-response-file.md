---
title: Plik polecenia BSCMAKE (plik odpowiedzi) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69fb144bed21b00fc07107f3fa8d5e64c1afb10d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716569"
---
# <a name="bscmake-command-file-response-file"></a>Plik polecenia BSCMAKE (Plik odpowiedzi)

Możesz podać część lub całość danych wejściowych wiersza polecenia w pliku poleceń. Określ plik polecenia, używając następującej składni:

```
BSCMAKE @filename
```

Tylko jedno polecenie pliku jest dozwolone. Można określić ścieżkę z *filename*. Należy poprzedzić *filename* ze znakiem (**\@**). BSCMAKE nie zakłada rozszerzenie. Można określić dodatkowe *sbrfiles* w wierszu polecenia po *filename*. Plik poleceń jest plik tekstowy, który zawiera dane wejściowe BSCMAKE w tej samej kolejności, jak należy je określić w wierszu polecenia. Oddzielne argumenty wiersza polecenia z jednego lub więcej miejsca do magazynowania, karty lub znakami nowego wiersza.

Następujące polecenie wywołuje BSCMAKE przy użyciu pliku polecenia:

```
BSCMAKE @prog1.txt
```

Oto przykładowy plik polecenia:

```
/n /v /o main.bsc /El
/S (
toolbox.h
verdate.h c:\src\inc\screen.h
)
file1.sbr file2.sbr file3.sbr file4.sbr
```

## <a name="see-also"></a>Zobacz też

[BSCMAKE — dokumentacja](../../build/reference/bscmake-reference.md)