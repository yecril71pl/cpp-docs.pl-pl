---
title: /PDBALTPATH (Użyj alternatywnej ścieżki PDB)
ms.date: 11/04/2016
f1_keywords:
- /pdbaltpath
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
ms.openlocfilehash: 660e39a97b9fed0c5a9228fe011e7c0fa2566e68
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820718"
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

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)<br/>
[/PDBPATH](pdbpath.md)
