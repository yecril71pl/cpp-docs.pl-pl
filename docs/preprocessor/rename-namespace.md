---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 6521fe0a5bfbe482bf2aed8f5a32221abdc6d6d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531602"
---
# <a name="renamenamespace"></a>rename_namespace

**Określonego język C++**

Zmienia nazwę przestrzeni nazw, który znajduje się zawartość biblioteki typów.

## <a name="syntax"></a>Składnia

```
rename_namespace("NewName")
```

### <a name="parameters"></a>Parametry

*Nowa nazwa*<br/>
Nowa nazwa przestrzeni nazw.

## <a name="remarks"></a>Uwagi

Trwa pojedynczy argument *NewName*, która określa nową nazwę dla przestrzeni nazw.

Aby usunąć przestrzeń nazw, należy użyć [no_namespace](../preprocessor/no-namespace.md) zamiast tego atrybutu.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)