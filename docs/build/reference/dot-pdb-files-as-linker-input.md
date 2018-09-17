---
title: . PDB, pliki jako dane wejściowe konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6b728903d2a270efc6b3eb736e45540651dae8c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706189"
---
# <a name="pdb-files-as-linker-input"></a>Pliki .Pdb — Wejście konsolidatora

Obiekt, pliki (.obj), skompilowane przy użyciu opcji/zi zawierają nazwę bazy danych programu (PDB). Nie określaj nazwy w pliku PDB obiektu do konsolidatora; ŁĄCZE o nazwie embedded można znaleźć pliku PDB, jeśli jest to konieczne. Dotyczy to również debugowania obiekty zawarte w bibliotece; plik PDB dla biblioteki debugowania musi być dostępny do konsolidatora wraz z biblioteki.

ŁĄCZE używa również pliku PDB do przechowywania informacji o debugowaniu dla pliku .exe lub .dll. PDB programu jest zarówno plik wyjściowy, jak i plik wejściowy, ponieważ łącze zaktualizowanie pliku PDB, gdy zostanie odbudowana program.

## <a name="see-also"></a>Zobacz też

[Pliki wejściowe LINK](../../build/reference/link-input-files.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)