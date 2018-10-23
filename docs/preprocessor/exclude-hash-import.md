---
title: Wykluczanie (#import) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- exclude
dev_langs:
- C++
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c345d9268f63a714eeae4beff78a7ac39ce545a1
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807903"
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