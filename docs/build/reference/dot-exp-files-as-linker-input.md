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
ms.openlocfilehash: 0f2f5c22752d6d938700228fc208c21b8f32cc7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293670"
---
# <a name="exp-files-as-linker-input"></a>Pliki .Exp — Wejście konsolidatora

Pliki eksportu (.exp) zawierają informacje na temat wyeksportowanych funkcji i danych elementów. Gdy LIB tworzy bibliotekę importu, również tworzy plik .exp. Użyj pliku .exp połączysz program, który umożliwia wyeksportowanie do i importuje z innego programu, bezpośrednio lub pośrednio. Jeśli łączysz się przy użyciu pliku .exp łącze nie generuje biblioteki importowanej, ponieważ przyjęto założenie, że LIB wcześniej utworzony. Aby uzyskać szczegółowe informacje o .EXP — pliki i bibliotekami importowanymi, zobacz [Praca z bibliotekami importowania i eksportowania plików](working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Zobacz także

[Pliki wejściowe LINK](link-input-files.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
