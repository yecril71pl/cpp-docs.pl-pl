---
title: Tworzenie pliku .Sbr
ms.date: 11/04/2016
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
ms.openlocfilehash: 6a2e685d33b108ce542fdc6e3e0565cc37299c1c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294073"
---
# <a name="creating-an-sbr-file"></a>Tworzenie pliku .Sbr

> [!WARNING]
> Mimo że BSCMAKE jest nadal zainstalowany za pomocą programu Visual Studio, nie jest już jest używany przez środowisko IDE. Od programu Visual Studio 2008 przeglądania i symbol informacji znajduje się automatycznie w plik sdf programu SQL Server, w folderze rozwiązania.

Pliki wejściowe dla BSCMAKE to pliki .sbr. Kompilator tworzy plik SBR dla każdego pliku obiektu (.obj) kompiluje. Podczas tworzenia lub zaktualizuj plik informacji przeglądania wszystkich plików SBR dla Twojego projektu musi być dostępny na dysku.

Utwórz plik .sbr z wszystkie dostępne informacje, należy określić [/FR](fr-fr-create-dot-sbr-file.md).

Aby utworzyć plik SBR, która nie zawiera symboli lokalnych, należy określić [/Fr](fr-fr-create-dot-sbr-file.md). Jeśli pliki SBR zawierają symbole lokalne, można nadal pominąć je w pliku .bsc przy użyciu firmy BSCMAKE [/El — opcja](bscmake-options.md)`.`

Można utworzyć pliku .sbr bez wykonywania pełnej kompilacji. Na przykład można określić /Zs — opcja kompilatora, aby wykonać sprawdzanie składni i nadal Generowanie pliku SBR, jeśli określisz /FR lub /Fr.

Proces kompilacji może być bardziej efektywne, jeśli pliki SBR najpierw są pakowane do usunięcia nieużywanych definicje. Kompilator automatycznie pakietów .SBR — pliki.

## <a name="see-also"></a>Zobacz także

[Kompilowanie pliku .Bsc](building-a-dot-bsc-file.md)
