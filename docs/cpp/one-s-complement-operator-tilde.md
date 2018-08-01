---
title: 'Jeden&#39;operatorem dopełnienia s: ~ | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- "~"
dev_langs:
- C++
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 79d34a4057ccbe5c10a6d22a14eed4317e62c464
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408636"
---
# <a name="one39s-complement-operator-"></a>Jeden&#39;operatorem dopełnienia s: ~
## <a name="syntax"></a>Składnia  
  
```  
~ cast-expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Operator dopełnienia jednostkowego (`~`), czasami nazywane operator "dopełnienia bitowego", daje bitowej, jeden na uzupełnienie swojego operandu. Każdego bitu, który ma wartość 1 w argumencie operacji jest 0, w wyniku. Z drugiej strony każdego bitu, który ma wartość 0 w argumencie operacji wynosi 1, w wyniku. Argument operacji do operator dopełnienia jednostkowego musi być typu całkowitego.  
  
## <a name="operator-keyword-for-"></a>Operator — słowo kluczowe dla ~  
 **Compl** operator jest odpowiednikiem tekstu `~`. Istnieją dwa sposoby dostępu do **compl** operatora w programach: dołączanie pliku nagłówka `iso646.h`, lub kompilowanie z [/za](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="example"></a>Przykład  
  
```cpp 
// expre_One_Complement_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main () {  
   unsigned short y = 0xFFFF;  
   cout << hex << y << endl;  
   y = ~y;   // Take one's complement  
   cout << hex << y << endl;  
}  
```  
  
 W tym przykładzie nowa wartość przypisana do `y` to uzupełnienie jedynkowe 0xFFFF lub 0x0000 wartości bez znaku.  
  
 Promocja typu całkowitego odbywa się w przypadku argumentów operacji typu całkowitego, a wynikowy typ jest typem, do którego argument jest podnoszony. Zobacz [konwersje standardowe](standard-conversions.md) więcej informacji na temat jak jest wykonywane podwyższenia poziomu.  
  
## <a name="see-also"></a>Zobacz także  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [C++ wbudowane operatory, pierwszeństwo i kojarzenie](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md)