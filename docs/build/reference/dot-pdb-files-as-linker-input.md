---
title: Pliki .Pdb — Wejście konsolidatora
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: 23974a9e20f8259c3a38af15664d328ded7ff7d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628903"
---
# <a name="pdb-files-as-linker-input"></a>Pliki .Pdb — Wejście konsolidatora

Obiekt, pliki (.obj), skompilowane przy użyciu opcji/zi zawierają nazwę bazy danych programu (PDB). Nie określaj nazwy w pliku PDB obiektu do konsolidatora; ŁĄCZE o nazwie embedded można znaleźć pliku PDB, jeśli jest to konieczne. Dotyczy to również debugowania obiekty zawarte w bibliotece; plik PDB dla biblioteki debugowania musi być dostępny do konsolidatora wraz z biblioteki.

ŁĄCZE używa również pliku PDB do przechowywania informacji o debugowaniu dla pliku .exe lub .dll. PDB programu jest zarówno plik wyjściowy, jak i plik wejściowy, ponieważ łącze zaktualizowanie pliku PDB, gdy zostanie odbudowana program.

## <a name="see-also"></a>Zobacz też

[Pliki wejściowe LINK](../../build/reference/link-input-files.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)