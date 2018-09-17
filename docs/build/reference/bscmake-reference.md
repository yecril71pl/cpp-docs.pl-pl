---
title: Bscmake — dokumentacja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9747d45f6593a689c8330b537945831735fb5e44
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724297"
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