---
title: -PDBALTPATH (Użyj alternatywnej ścieżki PDB) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbaltpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72c494745fa33c8feeb4955f4542e9db5ed22307
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718394"
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH (Użyj alternatywnej ścieżki PDB)

```
/PDBALTPATH:pdb_file_name
```

## <a name="arguments"></a>Argumenty

*pdb_file_name*<br/>
Ścieżka i nazwa pliku dla pliku PDB.

## <a name="remarks"></a>Uwagi

Użyj tej opcji, aby zapewnić alternatywną lokalizację pliku bazy danych programu (.pdb) w skompilowanym plikiem binarnym. Normalnie konsolidator rejestruje lokalizację pliku .pdb w pliki binarne, które tworzy. Ta opcja umożliwia Podaj inną ścieżkę i nazwę pliku dla pliku PDB. Informacjami o /PDBALTPATH nie zmienia lokalizację lub nazwę pliku .pdb rzeczywiste; Zmienia informacje, które konsolidator zapisuje w pliku binarnym. Dzięki temu można podać ścieżkę, która jest niezależna od struktury plików komputera kompilacji. Dwie typowe zastosowania tej opcji są Podaj ścieżkę sieciową lub pliku, który zawiera informacje o ścieżce.

Wartość *pdb_file_name* może być dowolny ciąg, zmienną środowiskową lub **_PDB %**. Konsolidator rozwinie zmiennej środowiskowej, takich jak **% SystemRoot %**, jego wartość. Konsolidator definiuje zmiennych środowiskowych **_PDB %** i **_EXT %**. **_PDB %** rozszerza się na nazwę pliku w pliku .pdb rzeczywista, bez żadnych informacji o ścieżce i **_EXT %** jest rozszerzeniem wygenerowany plik wykonywalny.

## <a name="see-also"></a>Zobacz też

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)<br/>
[/PDBPATH](../../build/reference/pdbpath.md)