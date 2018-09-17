---
title: -LINKERMEMBER | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /linkermember
dev_langs:
- C++
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0979009260381eb210e7992377bab8b5ae613338
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700612"
---
# <a name="linkermember"></a>/LINKERMEMBER

```
/LINKERMEMBER[:{1|2}]
```

## <a name="remarks"></a>Uwagi

Ta opcja wyświetla symbole publiczne zdefiniowane w bibliotece. Należy określić argument 1, aby wyświetlić symbole w kolejności obiektu, wraz z ich przesunięcia. Należy określić argument 2 przesunięcia i numery indeksu obiektów, a następnie wyświetlona lista symboli w kolejności alfabetycznej, wraz z indeks obiektów dla każdego. Aby uzyskać zarówno dane wyjściowe, należy określić /LINKERMEMBER bez argumentów o liczbie.

Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępna do użycia w plikach z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz też

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)