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
ms.openlocfilehash: 63f007e567f3c1db556ba6a7f0c1a354c449f31b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501013"
---
# <a name="creating-an-sbr-file"></a>Tworzenie pliku .Sbr

Pliki wejściowe dla BSCMAKE to pliki .sbr. Kompilator tworzy plik SBR dla każdego pliku obiektu (.obj) kompiluje. Podczas tworzenia lub zaktualizuj plik informacji przeglądania wszystkich plików SBR dla Twojego projektu musi być dostępny na dysku.

Utwórz plik .sbr z wszystkie dostępne informacje, należy określić [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).

Aby utworzyć plik SBR, która nie zawiera symboli lokalnych, należy określić [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Jeśli pliki SBR zawierają symbole lokalne, można nadal pominąć je w pliku .bsc przy użyciu firmy BSCMAKE [/El — opcja](../../build/reference/bscmake-options.md)`.`

Można utworzyć pliku .sbr bez wykonywania pełnej kompilacji. Na przykład można określić /Zs — opcja kompilatora, aby wykonać sprawdzanie składni i nadal Generowanie pliku SBR, jeśli określisz /FR lub /Fr.

Proces kompilacji może być bardziej efektywne, jeśli pliki SBR najpierw są pakowane do usunięcia nieużywanych definicje. Kompilator automatycznie pakietów .SBR — pliki.

## <a name="see-also"></a>Zobacz też

[Kompilowanie pliku .Bsc](../../build/reference/building-a-dot-bsc-file.md)