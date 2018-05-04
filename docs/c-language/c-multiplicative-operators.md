---
title: Operatory mnożenia języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1810cc9dd7a991e302e0e9e2db69f65aebebc613
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="c-multiplicative-operators"></a>Operatory mnożenia języka C
Operatory mnożenia wykonać mnożenia (**\***), dzielenia (**/**), a reszta (`%`) operacji.  
  
 **Składnia**  
  
 *wyrażenia mnożenia*:  
 *cast-expression*  
  
 *wyrażenia mnożenia***\****wyrażenie cast*   
  
 *wyrażenia mnożenia***/***wyrażenie cast*   
  
 *wyrażenia mnożenia***%***wyrażenie cast*   
  
 Argumenty operacji operatora pozostałej (`%`) musi być wartością całkowitą. ILOCZYN (**\***) i dzielenia (**/**) operatory może zająć argumentów operacji typu całkowitego lub zmiennoprzecinkową typ -; typy argumenty mogą być różne.  
  
 Operatory mnożenia Wykonaj popularne konwersje arytmetyczne w wypadku argumentów operacji. Typ wyniku jest typ operandy po konwersji.  
  
> [!NOTE]
>  Ponieważ konwersje wykonywane przez operatory multiplikatywne nie przewidują warunków przepełnienia lub niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji multiplikatywnej nie może być przedstawiony w typie operandów po konwersji.  
  
 Operatory mnożenia języka C są opisane poniżej:  
  
|Operator|Opis|  
|--------------|-----------------|  
|**\***|Operator mnożenia powoduje, że do mnożona dwóch argumentów.|  
|**/**|Operator dzielenia powoduje, że pierwszy argument operacji podzielony przez drugą. Jeśli są podzielone dwóch argumentów operacji całkowitą i nie jest liczbą całkowitą, zostanie obcięta zgodnie z następującymi zasadami:|  
||-Wynik dzielenie przez 0 jest niezdefiniowana ze standardem ANSI C. Kompilator Microsoft C generuje błąd w czasie kompilacji lub w czasie wykonywania.|  
||— Jeśli obydwa argumenty operacji są dodatnie lub unsigned, wynik jest obcinana do 0.|  
||— Jeśli którykolwiek argument operacji ma wartość ujemną, wynik operacji największa liczba całkowita mniejsza niż iloraz algebraicznych czy jest to najmniejsza liczba całkowita większa lub równa algebraicznych iloraz jest zdefiniowany implementacji. (Patrz poniższa sekcja Specific firmy Microsoft).|  
|`%`|Wynik operator reszty jest pozostałą, gdy pierwszy argument operacji jest dzielona przez drugą. Podczas podziału jest niedokładna, wynik jest określany przez następujące reguły:|  
||— Jeśli prawy operand jest zero, wynikiem jest niezdefiniowany.|  
||— Jeśli obydwa argumenty operacji są dodatnie lub unsigned, wynik jest dodatnią.|  
||— Jeśli którykolwiek argument operacji jest ujemna, wynikiem jest niedokładna wynik jest zdefiniowany implementacji. (Patrz poniższa sekcja Specific firmy Microsoft).|  
  
 **Microsoft Specific**  
  
 W regionie, w którym którykolwiek argument operacji jest ujemna kierunek obcięcie jest kierunku 0.  
  
 Jeśli każda operacja jest ujemna działu z operator reszty, wynik zawiera ten sam znak co dzielna (pierwszego operandu w wyrażeniu).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady są używane deklaracje pokazano poniżej:  
  
```  
int i = 10, j = 3, n;  
double x = 2.0, y;  
```  
  
 Operator mnożenia korzysta z tej instrukcji:  
  
```  
y = x * i;  
```  
  
 W takim przypadku `x` jest mnożona przez `i` aby nadać wartość 20.0. Wynik zawiera **podwójne** typu.  
  
```  
n = i / j;  
```  
  
 W tym przykładzie 10 jest podzielona przez 3. Wynik został obcięty kierunku 0 reaguje na wartość całkowitą 3.  
  
```  
n = i % j;  
```  
  
 Ta instrukcja przypisuje `n` Pozostała liczba całkowita, 1, gdy 10 jest dzielona przez 3.  
  
 **Microsoft Specific**  
  
 Znak pozostałej jest taka sama, jak znak dzielna. Na przykład:  
  
```  
50 % -6 = 2  
-50 % 6 = -2  
```  
  
 W każdym przypadku `50` i `2` mieć ten sam znak.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory mnożenia i Operator modulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)