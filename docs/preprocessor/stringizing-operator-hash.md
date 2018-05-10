---
title: Operator tworzenia ciągów (#) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7891b03fe80b5ad91ad52cf4577d237350d4584c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="stringizing-operator-"></a>Operator tworzenia ciągów (#)
Numer znaku lub operator "tworzenia ciągów" (**#**) konwertuje parametrów makra na literały ciągu bez rozwinięcie definicji parametru. Jest on używany tylko z makrami, które przyjmują argumenty. Jeżeli poprzedza on parametr formalny w definicji makra, rzeczywisty argument przekazywany przez wywołanie makra jest ujęty w znaki cudzysłowu i traktowany jako literał ciągu. Literał ciągu następnie zamienia każde wystąpienie kombinacji operatora tworzenia ciągu i parametru formalnego w ramach definicji makra.  
  
> [!NOTE]
>  Rozszerzenie Microsoft C (wersje 6.0 i starsze) dla standardu ANSI C, które wcześniej rozszerzało argumenty formalne makra pojawiające się wewnątrz literałów ciągu i stałych ciągu, nie jest już obsługiwane. Kod, który będzie zależał od tego rozszerzenia powinien ponownego napisania za pomocą tworzenia ciągów (**#**) operatora.  
  
Odstęp poprzedzający pierwszy token rzeczywistego argumentu i występujący po ostatnim tokenie rzeczywistego argumentu jest ignorowany. Wszelkie odstępy między tokenami w rzeczywistym argumencie są skracane do pojedynczego odstępu w wynikowym literale ciągu. Zatem jeśli komentarz występuje między dwoma tokenami w rzeczywistym argumencie, jest on skracany do jednego odstępu. Wynikowy literał ciągu jest automatycznie łączony z dowolnymi przylegającymi literałami ciągu, od których jest on oddzielony odstępem.  
  
Dalsze, jeśli znak zawartych w argumencie zwykle wymaga sekwencji unikowej, gdy jest używany w literale ciągu (na przykład znak cudzysłowu (**"**) ani ukośnika odwrotnego (**\\**) znaków), odwrotny niezbędne ucieczki automatycznie zostanie wstawiony przed znakiem.  
  
Operator stringizing Visual C++ nie zadziała poprawnie, gdy jest używany z ciągami, które obejmują sekwencji unikowych. W takim przypadku kompilator generuje [C2017 błąd kompilatora](../error-messages/compiler-errors-1/compiler-error-c2017.md).  
  
## <a name="example"></a>Przykład  
W poniższym przykładzie pokazano definicję makra, która zawiera operator tworzenia ciągu i główną funkcję, która wywołuje makro:  
  
Takie wywołania będą rozwijane podczas wstępnego przetwarzania, generując poniższy kod:  
  
```cpp  
int main() {  
   printf_s( "In quotes in the printf function call\n" "\n" );  
   printf_s( "\"In quotes when printed to the screen\"\n" "\n" );  
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );  
}  
```  
  
```cpp  
// stringizer.cpp  
#include <stdio.h>  
#define stringer( x ) printf_s( #x "\n" )  
int main() {  
   stringer( In quotes in the printf function call );   
   stringer( "In quotes when printed to the screen" );     
   stringer( "This: \"  prints an escaped double quote" );  
}  
```  
  
```Output  
In quotes in the printf function call  
"In quotes when printed to the screen"  
"This: \"  prints an escaped double quote"  
```  
  
## <a name="example"></a>Przykład  
W poniższym przykładzie pokazano sposób rozwijania parametru makra:  
  
```cpp  
// stringizer_2.cpp  
// compile with: /E  
#define F abc  
#define B def  
#define FB(arg) #arg  
#define FB1(arg) FB(arg)  
FB(F B)  
FB1(F B)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory preprocesora](../preprocessor/preprocessor-operators.md)