---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 7b3917a7114ca44d092f10a7831bb35bc64e9387
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039880"
---
# <a name="renamenamespace"></a>rename_namespace

**Określonego język C++**

Zmienia nazwę przestrzeni nazw, który znajduje się zawartość biblioteki typów.

## <a name="syntax"></a>Składnia

```
rename_namespace("NewName")
```

### <a name="parameters"></a>Parametry

*NewName*<br/>
Nowa nazwa przestrzeni nazw.

## <a name="remarks"></a>Uwagi

Trwa pojedynczy argument *NewName*, która określa nową nazwę dla przestrzeni nazw.

Aby usunąć przestrzeń nazw, należy użyć [no_namespace](../preprocessor/no-namespace.md) zamiast tego atrybutu.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)