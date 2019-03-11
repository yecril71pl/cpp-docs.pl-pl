---
title: Plik — Stałe
ms.date: 11/04/2016
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
ms.openlocfilehash: f0bf85dc8f27fca1720cde7f5a8b2029a791849c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739980"
---
# <a name="file-constants"></a>Plik — Stałe

## <a name="syntax"></a>Składnia

```
#include <fcntl.h>
```

## <a name="remarks"></a>Uwagi

Wyrażenia typu całkowitego tworzony na podstawie jednej lub więcej te stałe Określa typ Odczyt lub zapis operacji dozwolone. Jest on tworzony przez połączenie jednej lub więcej stałych z stałą tryb translacji.

Plik — stałe są następujące:

|Stała|Opis|
|-|-|
| `_O_APPEND`  | Powoduje przeniesienie wskaźnika pliku na koniec pliku przed wykonaniem każdej operacji zapisu.  |
| `_O_CREAT`  | Tworzy i otwiera nowy plik do zapisu; to nie obowiązuje, jeżeli plik określony przez *filename* istnieje.  |
| `_O_EXCL`  | Zwraca wartość błędu, jeśli plik określony przez *filename* istnieje. Ma zastosowanie tylko, gdy jest używane z `_O_CREAT`.  |
| `_O_RDONLY`  | Otwiera plik do odczytu. Jeśli ta flaga nie zostanie podany, ani `_O_RDWR` ani `_O_WRONLY` można podać.  |
| `_O_RDWR`  | Otwiera plik na odczyt i zapis; Jeśli ta flaga nie zostanie podany, ani `_O_RDONLY` ani `_O_WRONLY` można podać.  |
| `_O_TRUNC`  | Otwiera się i obcina istniejącego pliku do zera length; Plik musi mieć uprawnienia do zapisu. Zawartość pliku są niszczone. Jeśli ta flaga zostanie podany, nie można określić `_O_RDONLY`.  |
| `_O_WRONLY`  | Otwiera plik do zapisu. Jeśli ta flaga nie zostanie podany, ani `_O_RDONLY` ani `_O_RDWR` można podać.  |

## <a name="see-also"></a>Zobacz także

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
