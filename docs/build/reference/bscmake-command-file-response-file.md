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
ms.openlocfilehash: 6a55fd616a00aeb3ade229bf7cff8220f86085b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295048"
---
# <a name="bscmake-command-file-response-file"></a>Plik polecenia BSCMAKE (Plik odpowiedzi)

> [!WARNING]
> Mimo że BSCMAKE jest nadal zainstalowany za pomocą programu Visual Studio, nie jest już jest używany przez środowisko IDE. Od programu Visual Studio 2008 przeglądania i symbol informacji znajduje się automatycznie w plik sdf programu SQL Server, w folderze rozwiązania.

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
