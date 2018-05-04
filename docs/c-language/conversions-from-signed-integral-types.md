---
title: Konwersje z podpisanych typów całkowitych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8747f6c1bfde3f076101cc9330d73b1c76c1055b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
|**CHAR**1|**short**|Rozszerzanie logowania|  
|**char**|**long**|Rozszerzanie logowania|  
|**char**|**char bez znaku**|Zachowaj wzorzec; bit znaczącymi bitami traci funkcję jako bitem|  
|**char**|**short bez znaku**|Rozszerz logowania do **krótki**; przekonwertować **krótki** do **krótko bez znaku**|  
|**char**|**unsigned long**|Rozszerz logowania do **długi**; przekonwertować **długi** do **unsigned long**|  
|**char**|**float**|Rozszerz logowania do **długi**; przekonwertować **długi** do **float**|  
|**char**|**double**|Rozszerz logowania do **długi**; przekonwertować **długi** do **podwójne**|  
|**char**|**Liczba typu double**|Rozszerz logowania do **długi**; przekonwertować **długi** do **podwójne**|  
|**short**|**char**|Zachowaj mniej znaczącego bajtu|  
|**short**|**long**|Rozszerzanie logowania|  
|**short**|**char bez znaku**|Zachowaj mniej znaczącego bajtu|  
|**short**|**short bez znaku**|Zachowaj wzorca bitowego; bit znaczącymi bitami traci funkcję jako bitem|  
|**short**|**unsigned long**|Rozszerz logowania do **długi**; przekonwertować **długi** do **unsigned long**|  
|**short**|**float**|Rozszerz logowania do **długi**; przekonwertować **długi** do **float**|  
|**short**|**double**|Rozszerz logowania do **długi**; przekonwertować **długi** do **podwójne**|  
|**short**|**Liczba typu double**|Rozszerz logowania do **długi**; przekonwertować **długi** do **podwójne**|  
|**long**|**char**|Zachowaj mniej znaczącego bajtu|  
|**long**|**short**|Zachowaj znaczącymi bitami programu word|  
|**long**|**char bez znaku**|Zachowaj mniej znaczącego bajtu|  
|**long**|**short bez znaku**|Zachowaj znaczącymi bitami programu word|  
|**long**|**unsigned long**|Zachowaj wzorca bitowego; bit znaczącymi bitami traci funkcję jako bitem|  
|**long**|**float**|Reprezentuje jako **float**. Jeśli **długi** nie może być reprezentowany dokładnie, precyzyjnie zostaną utracone.|  
|**long**|**double**|Reprezentuje jako **podwójne**. Jeśli **długi** nie może być reprezentowany dokładnie jako **podwójne**, precyzyjnie zostaną utracone.|  
|**long**|**Liczba typu double**|Reprezentuje jako **podwójne**. Jeśli **długi** nie może być reprezentowany dokładnie jako **podwójne**, precyzyjnie zostaną utracone.|  
  
 1. Wszystkie **char** wpisy przyjęto założenie, że **char** typ ma znak domyślnie.  
  
 **Microsoft Specific**  
  
 Dla kompilatora C Microsoft 32-bitowa liczba całkowita jest odpowiednikiem **długi**. Konwersja **int** wartość będzie kontynuowana takie same jak w przypadku **długi**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje przypisań](../c-language/assignment-conversions.md)