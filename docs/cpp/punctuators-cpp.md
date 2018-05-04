---
title: Znaki interpunkcyjne (C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ecaa90598ce07cd0db52b7a4c30cfacc12566aba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="punctuators-c"></a>Znaki interpunkcyjne (C++)
Znaki interpunkcyjne w języku C++ mają znaczenie składni i semantyczne w kompilatorze, ale nie, z sobą, określono operacja, której wynikiem jest wartość. Niektóre znaki interpunkcyjne, samodzielnie lub w połączeniu, można być operatory języka C++ lub być istotne dla preprocesora.  

 Żadnego z następujących znaków są traktowane jako znaki interpunkcyjne:  

```  
! % ^ & * ( ) - + = { } | ~  
[ ] \ ; ' : " < > ? , . / #  
```  

 Znaki interpunkcyjne **[**, **()**, i **{}** muszą występować parami po [fazy tłumaczenia](../preprocessor/phases-of-translation.md) 4.  

## <a name="see-also"></a>Zobacz też  
 [Konwencje leksykalne](../cpp/lexical-conventions.md)
