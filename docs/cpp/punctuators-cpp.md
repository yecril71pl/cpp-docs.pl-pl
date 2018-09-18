---
title: Przerywniki (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 438b3f0469d1e8426b1e0ec2a19a63d1ae63c041
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039273"
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