---
title: /PDBPATH
ms.date: 11/04/2016
f1_keywords:
- /pdbpath
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
ms.openlocfilehash: f29b8e61fbfbdb0f373e3e7510cb3f1fe0b9cc2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319853"
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

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)<br/>
[/PDBALTPATH (Użyj alternatywnej ścieżki PDB)](pdbaltpath-use-alternate-pdb-path.md)
