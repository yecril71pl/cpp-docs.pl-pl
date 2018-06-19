---
title: Hierarchia i kolejność ocen | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- associativity of operators [C++]
- precedence [C++], operators
- data binding [C++], operator precedence
- operators [C++], precedence
ms.assetid: 201f7864-0c51-4c55-9d6f-39c5d013bcb0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84c3ec69c936605729f6813f28450ee1194951c7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392188"
---
# <a name="precedence-and-order-of-evaluation"></a>Hierarchia i kolejność ocen
Priorytet i łączność operatorów C wpłynąć na grupowanie i oceny operandów w wyrażeniach. Kolejność jest znaczący tylko wtedy, gdy istnieją inne operatory o priorytecie większej lub mniejszej. Wyrażenia z operatorami o wyższym priorytecie są sprawdzane jako pierwsze. Pierwszeństwo można również opisać za pomocą słowa "powiązania." Operatory o wyższym priorytecie są określane jako ma większego powiązania.  
  
 W poniższej tabeli przedstawiono priorytet i łączność (kolejności, w jakiej są oceniane operandy) operatorów C, listę w kolejności od najwyższego do najniższego. W przypadku, gdy pojawią się ze sobą kilka operatorów, mają taki sam priorytet i są obliczane zgodnie z ich łączność. Operatory w tabeli są opisane w sekcjach, począwszy od [operatory przyrostka](../c-language/postfix-operators.md). Pozostałej części tej sekcji zawiera ogólne informacje na temat priorytet i łączność.  
  
## <a name="precedence-and-associativity-of-c-operators"></a>Priorytet i łączność operatory języka C  
  
|Symbol <sup>1</sup>|Typ operacji|Łączność|  
|-------------|-----------------------|-------------------|  
|**\[ ] ( ) . ->**<br /><br />**++** **--** (przyrostka)|Wyrażenie|Od lewej do prawej|  
**sizeof & \* + - ~!**<br /><br />**++ —** (prefiks)|Jednoargumentowe|Od prawej do lewej|  
|*typecasts*|Jednoargumentowe|Od prawej do lewej|  
|**\* / %**|Mnożenia|Od lewej do prawej|  
|**+ -**|Dodatku|Od lewej do prawej|  
|**\<\< >>**|Operatory przesunięcia bitowego|Od lewej do prawej|  
|**\< > \<= >=**|Relacyjnych|Od lewej do prawej|  
|**== !=**|Równość|Od lewej do prawej|  
|**&**|Bitwise-AND|Od lewej do prawej|  
|**^**|Bitwise-exclusive-OR|Od lewej do prawej|  
|**&#124;**|Bitwise-inclusive-OR|Od lewej do prawej|  
|**&&**|Logiczne- i|Od lewej do prawej|  
|**&#124;&#124;**|Alternatywą logiczną|Od lewej do prawej|  
|**? :**|Wyrażenia warunkowego|Od prawej do lewej|  
|**= \*= /= %=**<br /><br /> **+= -= \<\<= >>= &=**<br /><br /> **^= &#124;=**|Przypisanie proste i złożone <sup>2</sup>|Od prawej do lewej|  
|**,**|Obliczanie sekwencyjne|Od lewej do prawej|  
  
 1. Operatory są wymienione w kolejności malejącej według priorytetu. Jeśli wiele operatorów pojawia się w tym samym wierszu lub w grupie, mają taki sam priorytet.  
  
 2. Wszystkie operatory proste i złożone przypisania mają taki sam priorytet.  
  
 Wyrażenie może zawierać wiele operatorów z równy priorytet. Gdy tych operatorów pojawią się na tym samym poziomie w wyrażeniu, oceny będzie kontynuowana zgodnie z kojarzenie operatora od prawej do lewej lub od lewej do prawej. Kierunek oceny nie ma wpływu na wyniki wyrażeń zawierających więcej niż jeden mnożenia (**\***), dodanie (**+**), lub dane binarne bitowe (**& &#124; ^**) — operator na tym samym poziomie. Kolejność operacji nie jest zdefiniowany przez język. Kompilator jest bezpłatny ocenić takich wyrażeń w dowolnej kolejności, kompilator może zagwarantować spójne wyniki.  
  
 Tylko obliczania sekwencyjnego (**,**) logicznej- i (**&&**), operatora logicznego OR (`||`), wyrażenia warunkowego (**?:**) i wywołania funkcji Operatory stanowią punkty sekwencji i w związku z tym gwarantuje kolejność ocen dla ich argumentów operacji. Operator wywołania funkcji jest zestawem nawiasów po identyfikator funkcji. Operator obliczania sekwencyjnego (**,**) może ocenić argumentów od lewej do prawej. (Należy pamiętać, że operator przecinka w wywołaniu funkcji nie jest taka sama jak operator obliczania sekwencyjnego i nie zapewnia takiej gwarancji). Aby uzyskać więcej informacji, zobacz [punkty sekwencji](../c-language/c-sequence-points.md).  
  
 Operatory logiczne gwarantuje również oceny operandy od lewej do prawej. Jednak umożliwiają podawanie wartości najmniejszą liczbę argumentów operacji potrzebne do określenia wynik wyrażenia. Jest on nazywany "zwarcia" oceny. W związku z tym niektóre argumenty wyrażenia nie może obliczyć. Na przykład w wyrażeniu  
  
`x && y++`  
  
 drugi argument operacji `y++`, jest oceniane tylko wtedy, gdy `x` ma wartość true (różną od zera). W związku z tym `y` nie jest zwiększany, jeśli `x` ma wartość false (0).  
  
## <a name="examples"></a>Przykłady
  
 Na poniższej liście przedstawiono, jak kompilator automatycznie wiąże kilka przykładowych wyrażeń:  

|Wyrażenie|Automatyczne powiązania|  
|----------------|-----------------------|  
|& b &#124; &#124; c|(& (b). &#124; &#124; c|  
|= b &#124; &#124; c|= (b &#124; &#124; c).|  
|q & & r &#124; &#124; s--|(q & & r) &#124; &#124; s--|  

 W pierwszym wyrażeniu operatora testu koniunkcji- i — operator (`&`) mają wyższy priorytet niż operator logiczny OR (`||`), więc `a & b` formularzy pierwszy argument operacji operatora logicznego OR.  
  
 Drugie wyrażenie operator logiczny OR (`||`) mają wyższy priorytet niż operator przypisania prostego (`=`), więc `b || c` są grupowane jako prawostronny operand przypisania. Należy pamiętać, że wartość przypisaną do `a` jest równa 0 lub 1.  
  
 Trzeci wyrażenie zawiera wyrażenie poprawnie sformułowany, które może wygenerować nieoczekiwany wynik. Logiczny- i — operator (`&&`) mają wyższy priorytet niż operator logiczny OR (`||`), więc `q && r` są grupowane jako argumentu. Ponieważ operatorów logicznych zagwarantować oceny operandy od lewej do prawej, `q && r` jest oceniane przed `s--`. Jednak jeśli `q && r` ma wartość niezerową, `s--` nie jest obliczane i `s` nie jest zmniejszany. Jeśli nie zmniejszanie `s` spowodowałoby problem w programie `s--` powinny się wyświetlać jako pierwszy argument operacji wyrażenia, lub `s` powinna być zmniejszana w oddzielnych operacji.  
  
 Poniższe wyrażenie jest niedozwolony i tworzy diagnostycznych wiadomości w czasie kompilacji:  
  
|Niedozwolone wyrażenie|Domyślne grupowanie|  
|------------------------|----------------------|  
|p == 0? p += 1: p += 2|(p == 0? p += 1: p) += 2|  
  
 W tym wyrażeniu operatora równości (`==`) ma pierwszeństwo, dlatego `p == 0` są grupowane jako argumentu. Operator wyrażenia warunkowego (`? :`) dalej najwyższy priorytet. Jego pierwszy argument operacji jest `p == 0`, a jej drugi argument operacji jest `p += 1`. Jednak ostatni argument operacji operatora wyrażenia warunkowego jest traktowany jako `p` zamiast `p += 2`, od momentu wystąpienia `p` dokładniejsze wiąże operator wyrażenia warunkowego niż operator przypisania złożone. Występuje błąd składni, ponieważ `+= 2` nie ma lewostronny operand. Należy Użyj nawiasów w celu uniknięcia błędów tego rodzaju i tworzy czytelność kodu. Na przykład można użyć nawiasów w sposób przedstawiony poniżej Popraw i wyjaśnić w poprzednim przykładzie:  
  
`( p == 0 ) ? ( p += 1 ) : ( p += 2 )`  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory języka C](../c-language/c-operators.md)
