---
title: Stałe pola ścieżki
ms.date: 11/04/2016
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
ms.openlocfilehash: 89609de3fc5584a960480bff83566f5e38c8be1f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62342487"
---
# <a name="path-field-limits"></a>Stałe pola ścieżki

## <a name="syntax"></a>Składnia

```cpp
#include <stdlib.h>
```

## <a name="remarks"></a>Uwagi

Te stałe zdefiniuj maksymalną długość ścieżki i poszczególnych pól w ścieżce.

|Stała|Znaczenie|
|--------------|-------------|
|`_MAX_DIR`|Maksymalna długość składnika katalogu|
|`_MAX_DRIVE`|Maksymalna długość składnika dysku|
|`_MAX_EXT`|Maksymalna długość składnika rozszerzenia|
|`_MAX_FNAME`|Maksymalna długość składnika, nazwa_pliku|
|`_MAX_PATH`|Maksymalna długość pełnej ścieżki|

> [!NOTE]
> Środowisko wykonawcze języka C obsługuje długości ścieżki maksymalnie wynosić 32 768 znaków długości, ale zależy od systemu operacyjnego, w szczególności systemu plików, do obsługi tych ścieżek dłużej. Suma pola nie powinna przekraczać `_MAX_PATH` pełnych wstecznej zgodności z FAT32 systemów plików. System plików NTFS w Windows obsługuje ścieżki maksymalnie wynosić 32 768 znaków długości, ale tylko wtedy, gdy za pomocą interfejsów API Unicode. Korzystając z długie nazwy ścieżek, prefiks ścieżki ze znakami \\ \\? \ i używanie wersje Unicode funkcje języka C środowiska uruchomieniowego.

## <a name="see-also"></a>Zobacz także

[Stałe globalne](../c-runtime-library/global-constants.md)