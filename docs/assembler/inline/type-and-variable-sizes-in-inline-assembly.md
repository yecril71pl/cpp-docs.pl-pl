---
title: Typ i rozmiary zmiennych w zestawie wbudowanym | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- length
- Type
dev_langs: C++
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee9edf9430c0333317a767e8f8c114453a6d80f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Typ i rozmiary zmiennych w zestawie wbudowanym
**Dotyczące firmy Microsoft**  
  
 **Długość**, **rozmiar**, i **typu** operatorów mają ograniczoną znaczenie w zestawie wbudowanym. Nie można ich używać na wszystkich z `DUP` — operator (ponieważ nie można zdefiniować danych za pomocą dyrektywy MASM lub operatory). Ale można je znaleźć rozmiar C lub C++ zmienne lub typów:  
  
-   **Długość** operator może zwracać liczbę elementów w tablicy. Zwraca wartość 1 dla zmiennych tablicy.  
  
-   **Rozmiar** operator może zwrócić rozmiar zmiennej języka C lub C++. Rozmiar zmiennej jest iloczyn jego **długość** i **typu**.  
  
-   **Typu** operator może zwrócić rozmiar typu C lub C++ lub zmiennej. Jeśli zmienna jest tablicą, **typu** zwraca rozmiar pojedynczego elementu tablicy.  
  
 Na przykład, jeśli program ma 8 element `int` tablicy  
  
```  
int arr[8];  
```  
  
 rozmiar uzyskanie następujących wyrażeń C i zestawu `arr` i jej elementów.  
  
|__asm|C|Rozmiar|  
|-------------|-------|----------|  
|**DŁUGOŚĆ** arr|`sizeof`(arr) /`sizeof`(arr[0])|8|  
|**ROZMIAR** arr|`sizeof`(arr)|32|  
|**Typ** arr|`sizeof`(arr[0])|4|  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)