---
title: Odwołanie BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: 1f321d51d1b880ea634c835567767c528aca041b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509477"
---
# <a name="bscmake-reference"></a>Odwołanie BSCMAKE

> [!WARNING]
> Mimo że BSCMAKE jest nadal zainstalowany za pomocą programu Visual Studio, nie jest już jest używany przez środowisko IDE. Od programu Visual Studio 2008 przeglądania i symbol informacji znajduje się automatycznie w plik sdf programu SQL Server, w folderze rozwiązania.

Narzędzie konserwacji przeglądarki Microsoft informacji (BSCMAKE. Z rozszerzeniem EXE) tworzy pliku informacyjnego przeglądarki (.bsc) na podstawie plików SBR utworzony podczas kompilacji. Niektóre narzędzia innych firm przy użyciu .BSC — pliki do analizy kodu.

Podczas tworzenia programu, można utworzyć pliku informacyjnego przeglądarki programu automatycznie, przy użyciu BSCMAKE, aby utworzyć plik. Nie musisz wiedzieć, jak uruchomić BSCMAKE, jeśli utworzysz plik informacji przeglądania w środowisku programowania Visual C++. Możesz przeczytać ten temat, aby poznać dostępne opcje.

Jeśli kompilujesz program poza środowiskiem programowania, można utworzyć .bsc niestandardowych, które można sprawdzić, w środowisku. Uruchom BSCMAKE na pliki SBR, które utworzono podczas kompilacji.

> [!NOTE]
>  To narzędzie można uruchomić tylko w wierszu polecenia programu Visual Studio Developer. Nie można uruchomić go z wiersza poleceń systemu lub Eksploratora plików.

Ta sekcja zawiera następujące tematy:

- [Kompilowanie plików przeglądania informacji: Przegląd](../../build/reference/building-browse-information-files-overview.md)

- [Kompilowanie pliku .bsc](../../build/reference/building-a-dot-bsc-file.md)

- [Wiersz polecenia BSCMAKE](../../build/reference/bscmake-command-line.md)

- [Plik polecenia BSCMAKE](../../build/reference/bscmake-command-file-response-file.md)

- [Opcje BSCMAKE](../../build/reference/bscmake-options.md)

- [Kody zakończenia BSCMAKE](../../build/reference/bscmake-exit-codes.md)

## <a name="see-also"></a>Zobacz też

[Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)