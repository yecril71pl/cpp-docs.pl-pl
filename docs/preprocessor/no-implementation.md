---
title: no_implementation
ms.date: 11/04/2016
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: d4e55d06bef823d28c5deb3467654bc530a3853e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456787"
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

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)