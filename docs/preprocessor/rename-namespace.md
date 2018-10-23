---
title: rename_namespace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 966c6dda7e5e0bd28e78f37967397c3b64e4e55c
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808475"
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