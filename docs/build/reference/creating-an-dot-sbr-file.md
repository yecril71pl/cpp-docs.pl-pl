---
title: Tworzenie. Plik SBR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac872dd13458c3fe15971f30a72b06e5510c5bd0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723687"
---
# <a name="creating-an-sbr-file"></a>Tworzenie pliku .Sbr

Pliki wejściowe dla BSCMAKE to pliki .sbr. Kompilator tworzy plik SBR dla każdego pliku obiektu (.obj) kompiluje. Podczas tworzenia lub zaktualizuj plik informacji przeglądania wszystkich plików SBR dla Twojego projektu musi być dostępny na dysku.

Utwórz plik .sbr z wszystkie dostępne informacje, należy określić [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).

Aby utworzyć plik SBR, która nie zawiera symboli lokalnych, należy określić [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Jeśli pliki SBR zawierają symbole lokalne, można nadal pominąć je w pliku .bsc przy użyciu firmy BSCMAKE [/El — opcja](../../build/reference/bscmake-options.md)`.`

Można utworzyć pliku .sbr bez wykonywania pełnej kompilacji. Na przykład można określić /Zs — opcja kompilatora, aby wykonać sprawdzanie składni i nadal Generowanie pliku SBR, jeśli określisz /FR lub /Fr.

Proces kompilacji może być bardziej efektywne, jeśli pliki SBR najpierw są pakowane do usunięcia nieużywanych definicje. Kompilator automatycznie pakietów .SBR — pliki.

## <a name="see-also"></a>Zobacz też

[Kompilowanie pliku .Bsc](../../build/reference/building-a-dot-bsc-file.md)