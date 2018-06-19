---
title: Tablice jednowymiarowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- brackets [ ]
- brackets [ ], arrays
- one-dimensional arrays
- arrays [C++], one-dimensional
- square brackets [ ]
- square brackets [ ], arrays
- subscript expressions
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8d7366a2c0a1b8ae9ed4e37eaaa89de9baf794d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388909"
---
# <a name="one-dimensional-arrays"></a>Tablice jednowymiarowe
Wyrażenie przyrostek następuje wyrażenia w nawiasach kwadratowych (**[**) jako reprezentacja elementu tablicy obiektów. Wyrażenia indeksu dolnego reprezentuje wartość na adres, który jest *wyrażenie* umieszcza poza *wyrażenie przyrostek* wyrażone jako  
  
```  
  
postfix-expression  
[  
expression  
]  
  
```  
  
 Zazwyczaj reprezentowany przez wartość *wyrażenie przyrostek* jest wartość wskaźnika, na przykład identyfikator tablicy i *wyrażenie* jest wartością całkowitą. Wszystko jest jednak wymagana Składnia tego jedno z wyrażeń jest typu wskaźnika i innych być typu całkowitego. W związku z tym może być wartością całkowitą w *wyrażenie przyrostek* pozycji i wartości wskaźnika, które mogą być w nawiasach w *wyrażenie*, lub pozycji "indeksu". Na przykład ten kod jest prawnych:  
  
```  
// one_dimensional_arrays.c  
int sum, *ptr, a[10];  
int main() {  
   ptr = a;  
   sum = 4[ptr];  
}  
```  
  
 Wyrażenia indeksu dolnego są zazwyczaj używane do odwoływania się do elementów tablicy, ale indeks dolny można zastosować do dowolnego wskaźnika. Niezależnie od kolejność wartości, *wyrażenie* musi być ujęta w nawiasy kwadratowe (**[**).  
  
 Obliczanie wyrażenia indeksu dolnego dodając wartość całkowitą wartość wskaźnika, a następnie zastosowanie operator pośredni (**\***) do wyniku. (Zobacz [operatory pośrednie i operatorów adresu](../c-language/indirection-and-address-of-operators.md) omówienie operator pośredni.) W efekcie dla tablicą jednowymiarową następujące cztery wyrażenia są równoważne, przy założeniu, że `a` wskaźnik i `b` jest liczbą całkowitą:  
  
```  
a[b]  
*(a + b)  
*(b + a)  
b[a]  
```  
  
 Zgodnie z reguły konwersji dla operator dodawania (podano w [operatory dodatku](../c-language/c-additive-operators.md)), wartości całkowite jest konwertowana na adres przesunięcie mnożąc długość typu adresowane przez wskaźnik.  
  
 Na przykład, załóżmy, że identyfikator `line` odwołuje się do tablicy `int` wartości. Poniższa procedura służy do obliczenia wyrażenia indeksu dolnego `line[ i ]`:  
  
1.  Wartość całkowita `i` jest mnożona przez liczbę bajtów zdefiniowany jako długość `int` elementu. Wartość przekonwertowanego `i` reprezentuje `i` `int` pozycji.  
  
2.  Ta wartość przekonwertowanego jest dodawana do oryginalnej wartości wskaźnika (`line`) umożliwiające uzyskanie adres, który jest przesuwane `i` `int` umieszcza z `line`.  
  
3.  Operator pośredni jest stosowany do nowego adresu. Wynik jest wartością elementu tablicy w tym miejscu (intuicyjnie `line [ i ]`).  
  
 Wyrażenia indeksu `line[0]` reprezentuje wartość elementu pierwszego wiersza, ponieważ przesunięcie z adresu reprezentowany przez `line` ma wartość 0. Podobnie, wyrażenie, takie jak `line[5]` odwołuje się do pozycji przesunięcie pięciu elementu z wiersza lub szóstego element tablicy.  
  
## <a name="see-also"></a>Zobacz też  
 [Operator indeksu dolnego:](../cpp/subscript-operator.md)