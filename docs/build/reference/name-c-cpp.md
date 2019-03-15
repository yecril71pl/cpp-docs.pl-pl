---
title: NAZWA (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: d0813befc622db72e095c449794405fc5d58465b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812190"
---
# <a name="name-cc"></a>NAZWA (C/C++)

Określa nazwę pliku głównego produktu.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>Uwagi

Sposób równoważny, aby określić nazwę pliku wyjściowego jest za pomocą [/OUT](out-output-file-name.md) — opcja konsolidatora i sposób równoważny, aby ustawić adres podstawowy jest [/BASE](base-base-address.md) — opcja konsolidatora. Jeśli są określone oba/OUT przesłania **nazwa**.

Jeśli tworzysz bibliotekę DLL, nazwa mają wpływ tylko na nazwy biblioteki DLL.

## <a name="see-also"></a>Zobacz także

[Zasady dla instrukcji definicji modułu](rules-for-module-definition-statements.md)
