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
ms.openlocfilehash: 8db9961bd2d5b5b3ea9d3addad3c26737b4f5199
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171401"
---
# <a name="path-field-limits"></a>Stałe pola ścieżki

## <a name="syntax"></a>Składnia

```cpp
#include <stdlib.h>
```

## <a name="remarks"></a>Uwagi

Te stałe definiują maksymalną długość ścieżki i dla poszczególnych pól w ścieżce.

|Stały|Znaczenie|
|--------------|-------------|
|`_MAX_DIR`|Maksymalna długość składnika katalogu|
|`_MAX_DRIVE`|Maksymalna długość składnika dysku|
|`_MAX_EXT`|Maksymalna długość składnika rozszerzenia|
|`_MAX_FNAME`|Maksymalna długość elementu filename|
|`_MAX_PATH`|Maksymalna długość pełnej ścieżki|

> [!NOTE]
> Środowisko uruchomieniowe języka C obsługuje długość ścieżki do 32768 znaków, ale jest do systemu operacyjnego, w odróżnieniu od systemu plików, do obsługi tych większej ścieżki. Suma pól nie powinna przekraczać `_MAX_PATH`, aby zapewnić pełną zgodność z poprzednimi wersjami z systemami plików FAT32. System plików systemu Windows NTFS obsługuje ścieżki o długości do 32768 znaków, ale tylko w przypadku korzystania z interfejsów API Unicode. W przypadku używania długich nazw ścieżek prefiks ścieżki ze znakami \\\\? \ i użyj wersji Unicode funkcji środowiska uruchomieniowego języka C.

## <a name="see-also"></a>Zobacz też

[Stałe globalne](../c-runtime-library/global-constants.md)
