---
title: Stałe pliku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e026de7b18d6809251e49f71d382c741f62be512
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028975"
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

## <a name="see-also"></a>Zobacz też

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)