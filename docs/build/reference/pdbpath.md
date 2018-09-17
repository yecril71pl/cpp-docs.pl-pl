---
title: -PDBPATH | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c9d93ef38ba444fd716bd3363a6605eae66dfec
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699678"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Nazwa pliku .dll lub .exe, dla którego chcesz znaleźć odpowiedniego pliku PDB.

**: PEŁNE**<br/>
(Opcjonalnie) Raportuje wszystkie katalogi, w którym nastąpiła próba można odnaleźć pliku .pdb.

## <a name="remarks"></a>Uwagi

/ PDBPATH wyszuka komputera wzdłuż tej samej ścieżki które debuger będzie szukać pliku .pdb i będzie zgłaszać które, jeśli pliki .pdb odnoszą się do pliku określonego w *filename*.

W przypadku używania debugera programu Visual Studio, może wystąpić problem z faktu, że debuger jest używany plik .pdb dla innej wersji pliku, który debugujesz.

/ PDBPATH wyszuka pliki .pdb wzdłuż następującej ścieżki:

- Sprawdź lokalizację, w której znajduje się plik wykonywalny.

- Sprawdź lokalizację pliku PDB zapisana w pliku wykonywalnego. Jest to zazwyczaj lokalizacji w momencie, których obraz został połączony.

- Sprawdź skonfigurowane w środowisku IDE programu Visual Studio na ścieżce wyszukiwania.

- Sprawdź wzdłuż ścieżek _NT_SYMBOL_PATH i _NT_ALT_SYMBOL_PATH zmiennych środowiskowych.

- Sprawdź w katalogu Windows.

## <a name="see-also"></a>Zobacz też

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)<br/>
[/PDBALTPATH (Użyj alternatywnej ścieżki PDB)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)