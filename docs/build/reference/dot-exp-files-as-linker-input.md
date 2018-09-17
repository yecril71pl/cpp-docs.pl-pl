---
title: . EXP, pliki jako dane wejściowe konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- exporting functions
- import libraries, linker files
- linking [C++], exports
- exporting functions, information about exported functions
- exporting data, export (.exp) files
- functions [C++], exporting
- .exp files [C++]
- EXP files
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4badc93f38d5ce76dcc294ad4ae216c8e3f6454c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724012"
---
# <a name="exp-files-as-linker-input"></a>Pliki .Exp — Wejście konsolidatora

Pliki eksportu (.exp) zawierają informacje na temat wyeksportowanych funkcji i danych elementów. Gdy LIB tworzy bibliotekę importu, również tworzy plik .exp. Użyj pliku .exp połączysz program, który umożliwia wyeksportowanie do i importuje z innego programu, bezpośrednio lub pośrednio. Jeśli łączysz się przy użyciu pliku .exp łącze nie generuje biblioteki importowanej, ponieważ przyjęto założenie, że LIB wcześniej utworzony. Aby uzyskać szczegółowe informacje o .EXP — pliki i bibliotekami importowanymi, zobacz [Praca z bibliotekami importowania i eksportowania plików](../../build/reference/working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Zobacz też

[Pliki wejściowe LINK](../../build/reference/link-input-files.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)