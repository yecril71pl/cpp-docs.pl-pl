---
title: Specyfikatory typu danych i odpowiedniki
ms.date: 11/04/2016
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
ms.openlocfilehash: 4003d9427c160b0e1c725cdc591190bd9777b3de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234933"
---
# <a name="data-type-specifiers-and-equivalents"></a>Specyfikatory typu danych i odpowiedniki

Ta książka zazwyczaj używa formularzy specyfikatorów typu wymienionych w poniższej tabeli, a nie w postaci długich, i zakłada, że `char` typ jest podpisany domyślnie. W związku z tym, w `char` tej książce, jest równoznaczny z **podpisem znaku**.

### <a name="type-specifiers-and-equivalents"></a>Specyfikatory typów i równoważne

|Specyfikator typu|Równoważne|
|--------------------|---------------------|
|**znak znaku**1|**char**|
|**Liczba cyfr ze znakiem**|ze **znakiem**, **int**|
|**podpisana krótka liczba całkowita**|**krótkie**, **podpisane krótkie**|
|**podpisana long int**|**długa**, **niepodpisana** cyfra|
|**unsigned char**|—|
|**unsigned int**|**bajt**|
|**unsigned short int**|**unsigned short**|
|**unsigned long int**|**unsigned long**|
|**float**|—|
|**Long Double**2|—|

1 Jeśli typ **znaku** jest domyślnie oznaczony jako niepodpisany (przez określenie opcji kompilatora/j), nie można skrócić znaku **podpisanego char** jako **char**.

2 w 32-bitowych i 64-bitowych systemach operacyjnych kompilator języka Microsoft C mapuje na **dużą** wartość typu **Double**.

**Specyficzne dla firmy Microsoft**

Można określić opcje kompilatora/J, aby zmienić domyślny typ **char** z podpisane na unsigned. Gdy ta opcja jest stosowana, **znak** oznacza takie samo jak **znak bez znaku**i należy użyć **podpisanego** słowa kluczowego, aby zadeklarować wartość znaku ze znakiem. Jeśli wartość **char** jest jawnie zadeklarowana jako podpisana, nie ma ona wpływu na tę opcję, a wartość jest podpisywana po rozszerzeniu na typ **int** . Typ **char** jest przedłużony o zero, gdy rozszerzany na typ **int** .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Specyfikatory typu C](../c-language/c-type-specifiers.md)
