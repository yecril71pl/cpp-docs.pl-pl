---
title: "Specyfikatory i odpowiedniki typów danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 596e3fcf4dab3f88abc17cac4bc32471e63b4bbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="data-type-specifiers-and-equivalents"></a>Specyfikatory typu danych i odpowiedniki
Ten podręcznik zazwyczaj używa formularze specyfikatorów typu wymienione w poniższej tabeli, a nie długich formularzy i przy założeniu, że `char` typ ma znak domyślnie. W związku z tym w niniejszym podręczniku `char` jest odpowiednikiem **podpisany char**.  
  
### <a name="type-specifiers-and-equivalents"></a>Specyfikatory typu i odpowiedniki  
  
|Specyfikator typu|Taryfowego(-ych)|  
|--------------------|---------------------|  
|**podpisana char**1|**char**|  
|**podpisanego elementu int**|**podpisana**, **int**|  
|**podpisana krótkich liczb całkowitych**|**krótki**, **krótko podpisany**|  
|**długie podpisanego elementu int**|**długie**, **podpisany długo**|  
|**char bez znaku**|—|  
|**unsigned int**|**bez znaku**|  
|**niepodpisane krótkich liczb całkowitych**|**short bez znaku**|  
|**unsigned int długa**|**unsigned long**|  
|**float**|—|  
|**Long double**2|—|  
  
 1 podczas wprowadzania **char** typu bez znaku domyślnie (określając /J — opcja kompilatora), nie można skrócić **podpisany char** jako **char**.  
  
 2 mapuje kompilator Microsoft C w 32-bitowych i 64-bitowych systemów operacyjnych, **podwójnej długości** na typ **podwójne**.  
  
 **Dotyczące firmy Microsoft**  
  
 Można określić opcję kompilatora /J, aby zmienić domyślny **char** typ ze znakiem do bez znaku. Gdy ta opcja jest włączona, **char** oznacza, że taka sama jak **unsigned char**, musisz użyć **podpisany** — słowo kluczowe, aby zadeklarować wartość podpisem znaków. Jeśli **char** wartość jest jawnie zadeklarowana podpisem, opcją / nie wpływa na jej i wartość jest znakiem, gdy rozszerzone, tak aby **int** typu. **Char** typ to zero rozszerzony podczas rozszerzone, tak aby **int** typu.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Specyfikatory typu C](../c-language/c-type-specifiers.md)