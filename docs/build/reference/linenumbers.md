---
title: -LINENUMBERS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /linenumbers
dev_langs:
- C++
helpviewer_keywords:
- LINENUMBERS dumpbin option
- line numbers
- -LINENUMBERS dumpbin option
- /LINENUMBERS dumpbin option
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9b969f51733d9eb4c45ac5609b42920765a7ad5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704057"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>Uwagi

Ta opcja wyświetla numery wierszy COFF. Numery wierszy istnieje w pliku obiektu, jeśli został skompilowany przy użyciu bazy danych programu (/Zi) zgodne z C7 (/ Z7), lub liczby tylko wiersz (/ ZD). Plik wykonywalny lub biblioteka DLL zawiera numery wierszy COFF, jeśli został połączony z Generuj informacje o debugowaniu (/ DEBUG).

Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępna do użycia w plikach z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz też

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)