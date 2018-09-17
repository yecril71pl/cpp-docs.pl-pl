---
title: NAZWA (C/C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc37a96e50c6cd5bae2cc60661db04f3b92d162b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715757"
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