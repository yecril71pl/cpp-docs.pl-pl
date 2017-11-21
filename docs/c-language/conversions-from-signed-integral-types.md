---
title: "Konwersje z podpisanych typów całkowitych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ccda8d6fa2573245f34a38f327395955bf92fdc2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="conversions-from-signed-integral-types"></a>Konwersje z podpisanych typów całkowitych
Gdy całkowita jest konwertowany na liczbę całkowitą bez znaku z równym lub większym rozmiarze, a wartość całkowita nie jest ujemna, wartość jest bez zmian. Konwersja zostało utworzone przez znak rozszerzanie liczbę całkowitą ze znakiem. Całkowita jest konwertowana na krótszą całkowita tworzy bardziej znaczących bitów. Wynik jest interpretowana jako wartość bez znaku, jak pokazano w poniższym przykładzie.  
  
```  
int i = -3;  
unsigned short u;  
  
u = i;   
printf_s( "%hu\n", u );  // Prints 65533  
  
```  
  
 Dane nie zostaną utracone po przekonwertowaniu do wartości zmiennoprzecinkowych, liczbę całkowitą ze znakiem z tą różnicą, że niektóre dokładności mogą zostać utracone po **długi int** lub **unsigned int długi** wartość jest konwertowana na **liczbzmiennoprzecinkowych** wartość.  
  
 Poniższa tabela zawiera podsumowanie konwersje z podpisanych typów całkowitych. W tej tabeli, przy założeniu, że **char** typ ma znak domyślnie. Jeśli używasz opcji kompilacji, aby zmienić domyślny dla **char** typ bez znaku, konwersje podany w [konwersje z niepodpisanych typów całkowitych](../c-language/conversions-from-unsigned-integral-types.md) tabeli dla **unsigned char**  typu zastosować zamiast konwersje w poniższej tabeli, konwersje z typów całkowitych podpisany.  
  
### <a name="conversions-from-signed-integral-types"></a>Konwersje z podpisanych typów całkowitych  
  
|Z|Do|Metoda|  
|----------|--------|------------|  
|**CHAR**1|**krótki**|Rozszerzanie logowania|  
|**char**|**długa**|Rozszerzanie logowania|  
|**char**|**char bez znaku**|Zachowaj wzorzec; bit znaczącymi bitami traci funkcję jako bitem|  
|**char**|**short bez znaku**|Rozszerz logowania do **krótki**; przekonwertować **krótki** do **krótko bez znaku**|  
|**char**|**unsigned long**|Rozszerz logowania do **długi**; przekonwertować **długi** do **unsigned long**|  
|**char**|**float**|Rozszerz logowania do **długi**; przekonwertować **długi** do **float**|  
|**char**|**podwójne**|Rozszerz logowania do **długi**; przekonwertować **długi** do **podwójne**|  
|**char**|**Liczba typu double**|Rozszerz logowania do **długi**; przekonwertować **długi** do **podwójne**|  
|**krótki**|**char**|Zachowaj mniej znaczącego bajtu|  
|**krótki**|**długa**|Rozszerzanie logowania|  
|**krótki**|**char bez znaku**|Zachowaj mniej znaczącego bajtu|  
|**krótki**|**short bez znaku**|Zachowaj wzorca bitowego; bit znaczącymi bitami traci funkcję jako bitem|  
|**krótki**|**unsigned long**|Rozszerz logowania do **długi**; przekonwertować **długi** do **unsigned long**|  
|**krótki**|**float**|Rozszerz logowania do **długi**; przekonwertować **długi** do **float**|  
|**krótki**|**podwójne**|Rozszerz logowania do **długi**; przekonwertować **długi** do **podwójne**|  
|**krótki**|**Liczba typu double**|Rozszerz logowania do **długi**; przekonwertować **długi** do **podwójne**|  
|**długa**|**char**|Zachowaj mniej znaczącego bajtu|  
|**długa**|**krótki**|Zachowaj znaczącymi bitami programu word|  
|**długa**|**char bez znaku**|Zachowaj mniej znaczącego bajtu|  
|**długa**|**short bez znaku**|Zachowaj znaczącymi bitami programu word|  
|**długa**|**unsigned long**|Zachowaj wzorca bitowego; bit znaczącymi bitami traci funkcję jako bitem|  
|**długa**|**float**|Reprezentuje jako **float**. Jeśli **długi** nie może być reprezentowany dokładnie, precyzyjnie zostaną utracone.|  
|**długa**|**podwójne**|Reprezentuje jako **podwójne**. Jeśli **długi** nie może być reprezentowany dokładnie jako **podwójne**, precyzyjnie zostaną utracone.|  
|**długa**|**Liczba typu double**|Reprezentuje jako **podwójne**. Jeśli **długi** nie może być reprezentowany dokładnie jako **podwójne**, precyzyjnie zostaną utracone.|  
  
 1. Wszystkie **char** wpisy przyjęto założenie, że **char** typ ma znak domyślnie.  
  
 **Dotyczące firmy Microsoft**  
  
 Dla kompilatora C Microsoft 32-bitowa liczba całkowita jest odpowiednikiem **długi**. Konwersja **int** wartość będzie kontynuowana takie same jak w przypadku **długi**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje przypisań](../c-language/assignment-conversions.md)