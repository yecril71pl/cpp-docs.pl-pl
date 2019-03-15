---
title: Plik polecenia BSCMAKE (Plik odpowiedzi)
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
ms.openlocfilehash: beb3d5696957f6b1af8168e3194e3943a1574be8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820315"
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

## <a name="see-also"></a>Zobacz także

[BSCMAKE — dokumentacja](bscmake-reference.md)
