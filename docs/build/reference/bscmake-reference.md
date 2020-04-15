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
ms.openlocfilehash: f95e34b9599de628463b9f92ebf8f01036237891
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320741"
---
# <a name="bscmake-reference"></a>Odwołanie BSCMAKE

> [!WARNING]
> Mimo że BSCMAKE jest nadal zainstalowany w programie Visual Studio, nie jest już używany przez IDE. Od programu Visual Studio 2008 informacje o przeglądaniu i symbolach są automatycznie przechowywane w pliku sdf programu SQL Server w folderze rozwiązania.

Narzędzie do konserwacji informacji przeglądania przez firmę Microsoft (BSCMAKE. EXE) tworzy plik informacji przeglądania (.bsc) z plików .sbr utworzonych podczas kompilacji. Niektóre narzędzia innych firm używają plików .bsc do analizy kodu.

Podczas tworzenia programu, można utworzyć plik informacji przeglądania dla programu automatycznie, za pomocą BSCMAKE do budowy pliku. Nie trzeba wiedzieć, jak uruchomić BSCMAKE, jeśli tworzysz plik informacji przeglądania w środowisku deweloperskim programu Visual Studio. Jednak można przeczytać ten temat, aby zrozumieć dostępne opcje.

Jeśli tworzysz program poza środowiskiem programistycznym, nadal można utworzyć niestandardowe .bsc, które można zbadać w środowisku. Uruchom BSCMAKE na plikach .sbr utworzonych podczas kompilacji.

> [!NOTE]
> To narzędzie można uruchomić tylko z wiersza polecenia programu Visual Studio Developer. Nie można go uruchomić z wiersza polecenia systemowego lub z Eksploratora plików.

Ta sekcja zawiera następujące tematy:

- [Kompilowanie plików przeglądania informacji: Przegląd](building-browse-information-files-overview.md)

- [Tworzenie pliku bsc](building-a-dot-bsc-file.md)

- [Wiersz polecenia BSCMAKE](bscmake-command-line.md)

- [Plik polecenia BSCMAKE](bscmake-command-file-response-file.md)

- [Opcje BSCMAKE](bscmake-options.md)

- [Kody wyjściowe BSCMAKE](bscmake-exit-codes.md)

## <a name="see-also"></a>Zobacz też

[Dodatkowe narzędzia do budowania MSVC](c-cpp-build-tools.md)
