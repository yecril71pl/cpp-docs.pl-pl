---
title: Pliki .Pdb — Wejście konsolidatora
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: 365f2955f5bc9e8082221a070af454c820c665f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273290"
---
# <a name="pdb-files-as-linker-input"></a>Pliki .Pdb — Wejście konsolidatora

Obiekt, pliki (.obj), skompilowane przy użyciu opcji/zi zawierają nazwę bazy danych programu (PDB). Nie określaj nazwy w pliku PDB obiektu do konsolidatora; ŁĄCZE o nazwie embedded można znaleźć pliku PDB, jeśli jest to konieczne. Dotyczy to również debugowania obiekty zawarte w bibliotece; plik PDB dla biblioteki debugowania musi być dostępny do konsolidatora wraz z biblioteki.

ŁĄCZE używa również pliku PDB do przechowywania informacji o debugowaniu dla pliku .exe lub .dll. PDB programu jest zarówno plik wyjściowy, jak i plik wejściowy, ponieważ łącze zaktualizowanie pliku PDB, gdy zostanie odbudowana program.

## <a name="see-also"></a>Zobacz także

[Pliki wejściowe LINK](link-input-files.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
