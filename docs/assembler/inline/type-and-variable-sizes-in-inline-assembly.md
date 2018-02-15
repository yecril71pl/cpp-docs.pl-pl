---
title: Typ i rozmiary zmiennych w zestawie wbudowanym | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- length
- Type
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38cbbd292ea662a725a8356b53fd0c1686e698e1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Typ i rozmiary zmiennych w zestawie wbudowanym
**Microsoft Specific**  
  
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