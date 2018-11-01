---
title: wykluczanie (#import)
ms.date: 10/18/2018
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: 1de1376fbe80147bc9fe01ea83bad81912431310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498257"
---
# <a name="exclude-import"></a>Wyklucz (\#importowanie)

**Określonego język C++**

Pomija pliki nagłówkowe biblioteki typów generowanych elementów.

## <a name="syntax"></a>Składnia

```
exclude("Name1"[, "Name2",...])
```

### <a name="parameters"></a>Parametry

*Nazwa1*<br/>
Pierwszy element do wykluczenia.

*Nazwa2*<br/>
Drugi element do wykluczenia (jeśli jest to konieczne).

## <a name="remarks"></a>Uwagi

Biblioteki typów mogą obejmować definicje elementy zdefiniowane w nagłówkach systemu lub inne biblioteki typów. Ten atrybut może być dowolną liczbę argumentów, jest element najwyższego poziomu typu biblioteki do wykluczenia.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)