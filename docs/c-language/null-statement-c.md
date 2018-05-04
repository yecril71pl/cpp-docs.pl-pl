---
title: Wartość null, Statement (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- semicolon, C null statement
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72e120fa412481a8313809bd5cdaf748de498bde
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="null-statement-c"></a>Instrukcja o wartości Null (C)
"Instrukcja o wartości null" jest instrukcji zawierającej tylko średnika; może być wyświetlany wszędzie tam, gdzie jest oczekiwany instrukcję. Nic się nie dzieje podczas wykonywania instrukcja o wartości null. Prawidłowy sposób kodowania instrukcja o wartości null jest:  
  
## <a name="syntax"></a>Składnia  
  
```  
  
;  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Instrukcje, takich jak **czy**, **dla**, **Jeśli**, i `while` wymagają aby instrukcji wykonywalnej jako treść instrukcji. Instrukcja o wartości null spełnia wymagania dotyczące składni w przypadkach, które nie są treść instrukcji merytorycznych.  
  
 Podobnie jak w przypadku innych instrukcji C, mogą obejmować etykiety przed instrukcja o wartości null. Etykietę elementu, który jest nie instrukcję, takich jak zamykający nawias klamrowy złożonej instrukcji można etykietę instrukcja o wartości null i wstaw go bezpośrednio przed element, aby uzyskać ten sam efekt.  
  
 W tym przykładzie przedstawiono instrukcja o wartości null:  
  
```  
for ( i = 0; i < 10; line[i++] = 0 )  
     ;  
```  
  
 W tym przykładzie wyrażenie pętli **dla** instrukcji `line[i++] = 0` inicjuje 10 pierwszych elementów `line` na 0. Treść instrukcji jest instrukcja o wartości null, ponieważ nie dalsze instrukcje są niezbędne.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../c-language/statements-c.md)