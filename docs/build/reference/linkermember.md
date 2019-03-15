---
title: /LINKERMEMBER
ms.date: 11/04/2016
f1_keywords:
- /linkermember
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
ms.openlocfilehash: a0456fd9ed1729b4a6cfa200a54ba211a64e94ea
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813282"
---
# <a name="linkermember"></a>/LINKERMEMBER

```
/LINKERMEMBER[:{1|2}]
```

## <a name="remarks"></a>Uwagi

Ta opcja wyświetla symbole publiczne zdefiniowane w bibliotece. Należy określić argument 1, aby wyświetlić symbole w kolejności obiektu, wraz z ich przesunięcia. Należy określić argument 2 przesunięcia i numery indeksu obiektów, a następnie wyświetlona lista symboli w kolejności alfabetycznej, wraz z indeks obiektów dla każdego. Aby uzyskać zarówno dane wyjściowe, należy określić /LINKERMEMBER bez argumentów o liczbie.

Tylko [/HEADERS](headers.md) — opcja polecenia DUMPBIN jest dostępna do użycia w plikach z [/GL](gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)
