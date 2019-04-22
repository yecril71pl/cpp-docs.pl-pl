---
title: wykluczanie (#import)
ms.date: 10/18/2018
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: d6a320089d5954b2cf1d0d96ae1f37656f2ddd58
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032391"
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

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)