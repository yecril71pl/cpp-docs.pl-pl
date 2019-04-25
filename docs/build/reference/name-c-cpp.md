---
title: NAZWA (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: d0813befc622db72e095c449794405fc5d58465b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320581"
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
