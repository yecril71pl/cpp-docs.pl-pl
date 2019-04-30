---
title: no_implementation
ms.date: 11/04/2016
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 26527ca69c66c73f5d41084dc42df5faa34481d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409814"
---
# <a name="noimplementation"></a>no_implementation
**Określonego język C++**

Powoduje pominięcie generowania nagłówka .tli, który zawiera implementacje funkcji elementów członkowskich otoki.

## <a name="syntax"></a>Składnia

```
no_implementation
```

## <a name="remarks"></a>Uwagi

Jeśli ten atrybut jest określony, nagłówku .tlh, za pomocą deklaracji do udostępnienia biblioteki typów elementów, zostanie wygenerowany bez `#include` instrukcję, aby uwzględnić plik nagłówka .tli.

Ten atrybut jest używany w połączeniu z [implementation_only —](../preprocessor/implementation-only.md).

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)