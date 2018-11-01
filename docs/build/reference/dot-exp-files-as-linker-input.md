---
title: Pliki .Exp — Wejście konsolidatora
ms.date: 11/04/2016
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
ms.openlocfilehash: 4f70aad2fa91431da771f8e5be47956ae2db45a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661936"
---
# <a name="exp-files-as-linker-input"></a>Pliki .Exp — Wejście konsolidatora

Pliki eksportu (.exp) zawierają informacje na temat wyeksportowanych funkcji i danych elementów. Gdy LIB tworzy bibliotekę importu, również tworzy plik .exp. Użyj pliku .exp połączysz program, który umożliwia wyeksportowanie do i importuje z innego programu, bezpośrednio lub pośrednio. Jeśli łączysz się przy użyciu pliku .exp łącze nie generuje biblioteki importowanej, ponieważ przyjęto założenie, że LIB wcześniej utworzony. Aby uzyskać szczegółowe informacje o .EXP — pliki i bibliotekami importowanymi, zobacz [Praca z bibliotekami importowania i eksportowania plików](../../build/reference/working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Zobacz też

[Pliki wejściowe LINK](../../build/reference/link-input-files.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)