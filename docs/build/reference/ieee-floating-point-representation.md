---
title: Odwzorowanie liczby zmiennoprzecinkowej IEEE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- float keyword
- real*8 value
- floating-point numbers, IEEE representation
- double data type, floating-point representation
- IEEE floating point representation
- real*10 value
- long double
- real*4 value
ms.assetid: 537833e8-fe05-49fc-8169-55fd0314b195
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17fae0cbb16208d5c7e7346f354f3501e4803d96
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="ieee-floating-point-representation"></a>Odwzorowanie liczby zmiennoprzecinkowej IEEE
Microsoft Visual C++ jest zgodne ze standardami liczbowych IEEE. Istnieją trzy wewnętrznego odmian liczb rzeczywistych. Rzeczywiste\*4 i rzeczywistych\*8 są używane w programie Visual C++. Rzeczywiste\*4 jest zadeklarowane za pomocą słowa **float**. Rzeczywiste\*8 jest zadeklarowane za pomocą słowa **podwójne**. W programowaniu Windows 32-bitowych `long double` mapowana na typ danych **podwójne**. Jest jednak obsługa języka zestawu obliczenia przy użyciu rzeczywistego * typ danych 10.  
  
 Wartości są przechowywane w następujący sposób:  
  
|Wartość|Przechowywane jako|  
|-----------|---------------|  
|rzeczywiste * 4|Zaloguj się bit, 8-bitową wykładnik, mantysa 23-bitowy|  
|rzeczywiste * 8|Zaloguj się bit, wykładnik 11-bitowy, mantysa 52-bitowy|  
|rzeczywiste * 10|Zaloguj się bit, wykładnik 15-bitowy, mantysa 64-bitowych|  
  
 W rzeczywistym * 4 i rzeczywistych\*8 formaty w mantysa, które nie są przechowywane w pamięci, dlatego mantysy są faktycznie 24 lub 53 bitów, nawet jeśli są przechowywane tylko 23 lub 52 bitów jest przyjmowane 1 wiodące. Rzeczywisty\*10 format zapisuje ten bit.  
  
 Wykładniki są ukierunkowane o połowę ich możliwych wartości. Oznacza to, że odjąć tego odchylenia od przechowywanych wykładnik, aby uzyskać rzeczywiste wykładnik. Jeśli przechowywane wykładnik jest mniejsza niż odchylenia, jest rzeczywiście ujemna wykładnik potęgi.  
  
 Wykładniki są ukierunkowane w następujący sposób:  
  
|Wykładnik|Ukierunkowane przez|  
|--------------|---------------|  
|8-bitową (rzeczywistych * 4)|127|  
|11-bitowego (rzeczywistych * 8)|1023|  
|15-bitowego (rzeczywistych * 10)|16383|  
  
 Wykładniki te nie są potęgami liczby dziesięciu; są one potęgami liczby dwa. Oznacza to 8-bitową wykładniki przechowywane może być maksymalnie 127 znaków. Wartość 2 ** 127 jest w przybliżeniu równy 10\*\*38 to rzeczywiste limit rzeczywistym\*4.  
  
 Mantysa są przechowywane jako ułamek binarne formularza 1.XXX.... Ta część ma wartość większa niż lub równa 1 i mniejsza niż wartość 2. Należy pamiętać, że liczb rzeczywistych zawsze są przechowywane w formie znormalizowaną; oznacza to mantysa zostanie lewej przesunięty w taki sposób, że bit znaczącymi bitami mantysa ma zawsze numer 1. Ponieważ ten bit ma zawsze numer 1, zakłada się (nie przechowywane) w rzeczywistym * 4 i rzeczywistych\*formatów 8. Binarny (dziesiętna) punktu zakłada się, że na prawo od początku 1.  
  
 Format, a następnie o różnych rozmiarach wygląda następująco:  
  
|Format|BAJT 1|BAJT 2|BAJT 3|BAJT 4|...|N BAJTÓW|  
|------------|------------|------------|------------|------------|---------|------------|  
|rzeczywiste * 4|`SXXX XXXX`|`XMMM MMMM`|`MMMM MMMM`|`MMMM MMMM`|||  
|rzeczywiste * 8|`SXXX XXXX`|`XXXX MMMM`|`MMMM MMMM`|`MMMM MMMM`|...|`MMMM MMMM`|  
|rzeczywiste * 10|`SXXX XXXX`|`XXXX XXXX`|`1MMM MMMM`|`MMMM MMMM`|...|`MMMM MMMM`|  
  
 `S` reprezentuje bitu znaku `X`w wykładnika bitów i `M`w mantysa bitów. Należy pamiętać, że po lewej stronie bit zakłada, że w rzeczywistym * 4 i rzeczywistych\*8 Formatuje, ale są dostępne jako "1" w rzeczywistym 3 BAJTÓW\*10 format.  
  
 Przesunięcie punktu binarne prawidłowo, najpierw unbias wykładnik i następnie przenoszenia binarne punktu z prawej strony lub odpowiedniej liczby bitów w lewo.  
  
## <a name="examples"></a>Przykłady  
 Poniżej przedstawiono kilka przykładów w rzeczywistym * 4 format:  
  
-   W poniższym przykładzie bitem jest zero, a przechowywane wykładnik 128 lub 100 0000 0 w pliku binarnego, który jest 127 plus 1. Mantysa przechowywanych jest (1). 000 0000 ... 0000 0000, który ma domniemanych wiodące 1 a danych binarnych punkt, dlatego rzeczywiste mantysa jest jednym.  
  
    ```  
                        SXXX XXXX XMMM MMMM ... MMMM MMMM  
    2   =  1  * 2**1  = 0100 0000 0000 0000 ... 0000 0000 = 4000 0000  
    ```  
  
-   Taki sam jak + 2 z tą różnicą, że ustawiono bitu znaku. Dotyczy to wszystkie liczby zmiennoprzecinkowej IEEE formatu.  
  
    ```  
    -2  = -1  * 2**1  = 1100 0000 0000 0000 ... 0000 0000 = C000 0000  
    ```  
  
-   Mantysa tego samego wykładnik zwiększa się o jeden (wartość obciążonej jest 129 lub 100 0000 1 w danych binarnych.  
  
    ```  
    4  =  1  * 2**2  = 0100 0000 1000 0000 ... 0000 0000 = 4080 0000  
    ```  
  
-   Wykładnik tego samego mantysa jest większy o połowę — jego (1). 100 0000... 0000 0000, czyli, ponieważ jest to ułamek binarne 1 1/2 (wartości cyfr ułamkowych to 1/2, 1/4, 1/8 i tak dalej).  
  
    ```  
    6  = 1.5 * 2**2  = 0100 0000 1100 0000 ... 0000 0000 = 40C0 0000  
    ```  
  
-   Wykładnik samej jako inne potęgami liczby dwa, mantysa jest jednym mniej niż dwa 127 lub 011 1111 1 w danych binarnych.  
  
    ```  
    1  = 1   * 2**0  = 0011 1111 1000 0000 ... 0000 0000 = 3F80 0000  
    ```  
  
-   Wykładnik obciążonej jest 126, 011 1111 0 w pliku binarnego i mantysy jest (1). 100 0000 ... 0000 0000, czyli 1 1/2.  
  
    ```  
    .75 = 1.5 * 2**-1 = 0011 1111 0100 0000 ... 0000 0000 = 3F40 0000  
    ```  
  
-   Tak samo jak dwa z wyjątkiem, że bit, który reprezentuje 1/4 jest ustawiana w mantysa.  
  
    ```  
    2.5 = 1.25 * 2**1 = 0100 0000 0010 0000 ... 0000 0000 = 4020 0000  
    ```  
  
-   1/10 jest ułamek powtarzających się w pliku binarnego. Mantysa jest po prostu shy w wersji 1.6, i obciążonej wykładnik o tym, że 1.6 podzielony przez 16 (jest 011 1101 1 w pliku binarnego, czyli 123 dziesiętnie). Wykładnik wartość true, to 123-127 = - 4, co oznacza, że współczynnik mnożenia 2 ** -4 = 1/16. Należy pamiętać, że przechowywane mantysa jest zaokrąglana w ostatnim bitowej — próba reprezentować liczby unrepresentable, jak to możliwe. (Przyczyna 1/10 do 1/100 są dokładnie można przedstawić w danych binarnych jest podobny do przyczyny, że nie można przedstawić w dziesiętnych jest 1/3.)  
  
    ```  
    0.1 = 1.6 * 2**-4 = 0011 1101 1100 1100 ... 1100 1101 = 3DCC CCCD  
    ```  
  
-   `0  = 1.0 * 2**-128 = all zeros--a special case.`  
  
## <a name="see-also"></a>Zobacz też  
 [Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność](../../build/reference/why-floating-point-numbers-may-lose-precision.md)