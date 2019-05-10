---
title: Odwołanie BSCMAKE
ms.date: 05/06/2019
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: 72ad297ee5a24bc0c7ffd3ed25959031d0b8a309
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220559"
---
# <a name="bscmake-reference"></a>Odwołanie BSCMAKE

> [!WARNING]
> Mimo że BSCMAKE jest nadal zainstalowany za pomocą programu Visual Studio, nie jest już jest używany przez środowisko IDE. Od programu Visual Studio 2008 przeglądania i symbol informacji znajduje się automatycznie w plik sdf programu SQL Server, w folderze rozwiązania.

Narzędzie konserwacji przeglądarki Microsoft informacji (BSCMAKE. Z rozszerzeniem EXE) tworzy pliku informacyjnego przeglądarki (.bsc) na podstawie plików SBR utworzony podczas kompilacji. Niektóre narzędzia innych firm przy użyciu .BSC — pliki do analizy kodu.

Podczas tworzenia programu, można utworzyć pliku informacyjnego przeglądarki programu automatycznie, przy użyciu BSCMAKE, aby utworzyć plik. Nie trzeba się dowiedzieć, jak uruchomić BSCMAKE, po utworzeniu pliku informacji przeglądania w środowisku programowania Visual Studio. Możesz przeczytać ten temat, aby poznać dostępne opcje.

Jeśli kompilujesz program poza środowiskiem programowania, można utworzyć .bsc niestandardowych, które można sprawdzić, w środowisku. Uruchom BSCMAKE na pliki SBR, które utworzono podczas kompilacji.

> [!NOTE]
>  To narzędzie można uruchomić tylko w wierszu polecenia programu Visual Studio Developer. Nie można uruchomić go z wiersza poleceń systemu lub Eksploratora plików.

Ta sekcja zawiera następujące tematy:

- [Kompilowanie plików przeglądania informacji: omówienie](building-browse-information-files-overview.md)

- [Kompilowanie pliku .bsc](building-a-dot-bsc-file.md)

- [Wiersz polecenia BSCMAKE](bscmake-command-line.md)

- [Plik polecenia BSCMAKE](bscmake-command-file-response-file.md)

- [Opcje BSCMAKE](bscmake-options.md)

- [Kody zakończenia BSCMAKE](bscmake-exit-codes.md)

## <a name="see-also"></a>Zobacz także

[MSVC dodatkowe narzędzia do kompilacji](c-cpp-build-tools.md)
