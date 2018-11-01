---
title: NAZWA (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: c05e82409d6b6e48390d54160e8ff23ada788d41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646202"
---
# <a name="name-cc"></a>NAZWA (C/C++)

Określa nazwę pliku głównego produktu.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>Uwagi

Sposób równoważny, aby określić nazwę pliku wyjściowego jest za pomocą [/OUT](../../build/reference/out-output-file-name.md) — opcja konsolidatora i sposób równoważny, aby ustawić adres podstawowy jest [/BASE](../../build/reference/base-base-address.md) — opcja konsolidatora. Jeśli są określone oba/OUT przesłania **nazwa**.

Jeśli tworzysz bibliotekę DLL, nazwa mają wpływ tylko na nazwy biblioteki DLL.

## <a name="see-also"></a>Zobacz też

[Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)