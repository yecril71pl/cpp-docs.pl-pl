---
title: Przerywniki (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
ms.openlocfilehash: cef34a17de99a189a590ac3f13c0db9563df643c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478275"
---
# <a name="punctuators-c"></a>Przerywniki (C++)

Przerywniki języka w języku C++ mają syntaktyczna i semantyczna znaczenie dla kompilatora, ale, sobie, określa operację, która daje wartość. Niektórych znaków autonomicznie lub w połączeniu, można być operatorów języka C++ lub być znaczące preprocesora.

Jedną z następujących znaków są uważane za przerywniki języka:

```
! % ^ & * ( ) - + = { } | ~
[ ] \ ; ' : " < > ? , . / #
```

Przerywniki języka **[**, **()**, i **{}** musi znajdować się w parach po [fazie tłumaczenia](../preprocessor/phases-of-translation.md) 4.

## <a name="see-also"></a>Zobacz także

[Konwencje leksykalne](../cpp/lexical-conventions.md)