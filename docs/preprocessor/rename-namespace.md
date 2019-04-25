---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 7b3917a7114ca44d092f10a7831bb35bc64e9387
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179766"
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

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)