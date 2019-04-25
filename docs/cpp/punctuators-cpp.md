---
title: Przerywniki (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
ms.openlocfilehash: cef34a17de99a189a590ac3f13c0db9563df643c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244236"
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