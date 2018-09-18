---
title: Typ danych Specyfikatory i odpowiedniki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68444d5ac8944e3c6679fce6397226d48206037f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092729"
---
# <a name="data-type-specifiers-and-equivalents"></a>Specyfikatory typu danych i odpowiedniki

Ten podręcznik ogólnie używa formy specyfikatory typów wymienionych w poniższej tabeli, a nie długich formularzy, a założono, że `char` typ ma znak domyślnie. W związku z tym, w tym podręczniku `char` jest odpowiednikiem **podpisany char**.

### <a name="type-specifiers-and-equivalents"></a>Specyfikatory typu i odpowiedniki

|Specyfikator typu|Taryfowego(-ych)|
|--------------------|---------------------|
|**podpisany char**1|**char**|
|**int podpisem**|**podpisana**, **int**|
|**podpisana krótka wartość całkowita**|**krótki**, **short ze znakiem**|
|**podpisana long int**|**długi**, **podpisany długo**|
|**unsigned char**|—|
|**unsigned int**|**Bez znaku**|
|**niepodpisane krótka wartość całkowita**|**short bez znaku**|
|**unsigned long int**|**unsigned long**|
|**float**|—|
|**double**2|—|

1 po ustawieniu **char** typ bez znaku domyślnie (określając opcję kompilatora/j.), nie można skrócić **podpisany char** jako **char**.

2 w 32-bitowych i 64-bitowych systemów operacyjnych, kompilator Microsoft C: mapuje **typu long double** na typ **double**.

**Microsoft Specific**

Można określić opcję kompilatora/j., aby zmienić domyślny **char** typu z podpisem do bez znaku. Gdy ta opcja jest aktywna, **char** oznacza taki sam jak **unsigned char**, musisz użyć **podpisany** — słowo kluczowe do deklarowania wartość podpisany znak. Jeśli **char** wartość jest zadeklarowany w sposób jawny podpisem, opcją/j. nie ma wpływu na jego i wartość jest rozszerzona o znak po rozszerzone do **int** typu. **Char** typ to zero rozszerzone podczas rozszerzone do **int** typu.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Specyfikatory typu C](../c-language/c-type-specifiers.md)