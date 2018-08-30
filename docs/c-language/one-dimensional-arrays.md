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
ms.openlocfilehash: bbb47eae81df8b1080480843bfa5a444f6eb989f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196979"
---
# <a name="one-dimensional-arrays"></a>Tablice jednowymiarowe
Wyrażenie przyrostkowe następują wyrażenia w nawiasach kwadratowych (**[**) jest indeksem reprezentacja elementu tablicy obiektów. Wyrażenie indeksu dolnego reprezentuje wartość pod adresem, który jest *wyrażenie* umieszcza poza *wyrażeniem przyrostkowym* wyrażone jako  
  
```  
postfix-expression [ expression ]
```  
  
 Zwykle reprezentowany przez wartość *wyrażeniem przyrostkowym* jest wartością wskaźnika, takich jak identyfikator tablicy, a *wyrażenie* jest wartością całkowitą. Jednakże, wszystko co jest wymagane składniowo tego jednego z wyrażeń jest typu wskaźnika i innych być typu całkowitego. Ten sposób może być wartością typu całkowitego *wyrażeniem przyrostkowym* położenie i wartość wskaźnika można w nawiasach w *wyrażenie*, lub pozycji "indeksu dolnego,". Na przykład ten kod jest dozwolony:  
  
```  
// one_dimensional_arrays.c  
int sum, *ptr, a[10];  
int main() {  
   ptr = a;  
   sum = 4[ptr];  
}  
```  
  
 Wyrażenia indeksu dolnego są zazwyczaj używane do odwoływania się do elementów tablicy, ale można zastosować indeks dolny dowolny wskaźnik. Niezależnie od kolejności wartości *wyrażenie* muszą być ujęte w nawiasy kwadratowe (**[**).  
  
 Wyrażenie indeksu dolnego jest oceniany przez dodanie wartość całkowitą wartość wskaźnika, a następnie zastosowanie operatora pośredniego (<strong>\*</strong>) do wyniku. (Zobacz [pośredni i Address-of operatory](../c-language/indirection-and-address-of-operators.md) dyskusję na temat operatora pośredniego.) W efekcie Jednowymiarowa tablica następujących czterech wyrażeń są równoważne przy założeniu, że `a` jest wskaźnikiem typu i `b` jest liczbą całkowitą:  
  
```  
a[b]  
*(a + b)  
*(b + a)  
b[a]  
```  
  
 Zgodnie z regułami konwersji, operator dodawania (podano [operatory addytywne](../c-language/c-additive-operators.md)), wartość całkowitą jest konwertowany na przesunięcie adresu mnożąc długość typ adresowany przez wskaźnik myszy.  
  
 Na przykład, załóżmy, że identyfikator `line` odwołuje się do tablicy `int` wartości. Poniższa procedura służy do obliczenia wyrażenia indeksu dolnego `line[ i ]`:  
  
1.  Wartość całkowita `i` jest mnożony przez liczbę bajtów zdefiniowane jako długość `int` elementu. Przekonwertowana wartości `i` reprezentuje `i` `int` pozycji.  
  
2.  Ta wartość przekonwertowanego jest dodawana do oryginalnej wartości wskaźnika (`line`) umożliwiające uzyskanie adres który jest przesunięty `i` `int` umieszcza z `line`.  
  
3.  Operator pośredni jest stosowany do nowego adresu. Wynik jest wartością elementu tablicy, w tym miejscu (intuicyjnie `line [ i ]`).  
  
 Wyrażenie indeksu dolnego `line[0]` reprezentuje wartość pierwszego elementu wiersza, ponieważ przesunięcie z adresu reprezentowanego przez `line` wynosi 0. Podobnie, wyrażenie, takie jak `line[5]` odwołuje się do pozycji przesunięcia pięciu elementu z wiersza lub szóstego elementu tablicy.  
  
## <a name="see-also"></a>Zobacz też  
 [Operator indeksu dolnego:](../cpp/subscript-operator.md)