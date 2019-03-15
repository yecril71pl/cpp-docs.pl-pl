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
ms.openlocfilehash: 75c3b926a605de66c876e9350218807031cd9a43
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810409"
---
# <a name="creating-an-sbr-file"></a>Tworzenie pliku .Sbr

Pliki wejściowe dla BSCMAKE to pliki .sbr. Kompilator tworzy plik SBR dla każdego pliku obiektu (.obj) kompiluje. Podczas tworzenia lub zaktualizuj plik informacji przeglądania wszystkich plików SBR dla Twojego projektu musi być dostępny na dysku.

Utwórz plik .sbr z wszystkie dostępne informacje, należy określić [/FR](fr-fr-create-dot-sbr-file.md).

Aby utworzyć plik SBR, która nie zawiera symboli lokalnych, należy określić [/Fr](fr-fr-create-dot-sbr-file.md). Jeśli pliki SBR zawierają symbole lokalne, można nadal pominąć je w pliku .bsc przy użyciu firmy BSCMAKE [/El — opcja](bscmake-options.md)`.`

Można utworzyć pliku .sbr bez wykonywania pełnej kompilacji. Na przykład można określić /Zs — opcja kompilatora, aby wykonać sprawdzanie składni i nadal Generowanie pliku SBR, jeśli określisz /FR lub /Fr.

Proces kompilacji może być bardziej efektywne, jeśli pliki SBR najpierw są pakowane do usunięcia nieużywanych definicje. Kompilator automatycznie pakietów .SBR — pliki.

## <a name="see-also"></a>Zobacz także

[Kompilowanie pliku .Bsc](building-a-dot-bsc-file.md)
