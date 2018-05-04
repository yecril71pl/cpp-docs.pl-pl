---
title: Wartości zwracane (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 53583524-b337-4228-a9c6-c9bf516babe8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec5097ab22ff82883117b6d224bce9c282ac9c8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="return-values-c"></a>Wartości zwracane (C++)
Wartość skalarną zwracany, który można umieścić w 64-bitowy jest zwracany za pomocą RAX — dotyczy to również __m64 typów. Typy non skalarna takich elementów przestawnych, symulacyjnych i typy wektorów, takich jak [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) są zwracane w XMM0. Stan nieużywanej bits w wartości zwracanej w RAX lub XMM0 jest niezdefiniowany.  
  
 Typy definiowane przez użytkownika może być zwracany przez wartości z globalnej funkcji i funkcji statycznego elementu członkowskiego. Zwracaną wartość RAX, typy danych zdefiniowane przez użytkownika musi mieć długość od 1, 2, 4, 8, 16, 32 lub 64-bitowy; nie zdefiniowane przez użytkownika Konstruktor, destruktor lub operatora przypisania kopii; nie członków prywatnych lub chronionych danych niestatycznych; nie elementy członkowskie danych niestatyczna typu referencyjnego; nie klas podstawowych; nie funkcji wirtualnych; i nie elementy członkowskie danych, które również nie spełniają tych wymagań. (Jest to zasadniczo definicji 03 C ++ POD typu. Ponieważ definicja została zmieniona w języku C ++ 11 standardowe, zaleca się używania `std::is_pod` dla tego testu.) W przeciwnym razie wywołującego przyjmuje na siebie odpowiedzialność przydzielania pamięci i przekazanie wskaźnika dla wartości zwracanej jako pierwszy argument. Kolejne argumenty są następnie przesunięte jednego argumentu z prawej strony. Wskaźnik tej samej musi zostać zwrócona przez funkcję wywołującą w RAX.  
  
 Poniższe przykłady pokazują, jak parametry i wartości zwracane są przekazywane dla funkcji o określonej deklaracje:  
  
## <a name="example-of-return-value-1---64-bit-result"></a>Przykład wynik 1-64-bitowej wartości zwracanej  
  
```Output  
__int64 func1(int a, float b, int c, int d, int e);  
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,  
// callee returns __int64 result in RAX.  
```  
  
## <a name="example-of-return-value-2---128-bit-result"></a>Przykład wynik 2-128-bitowej wartości zwracanej  
  
```Output  
__m128 func2(float a, double b, int c, __m64 d);   
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,   
// callee returns __m128 result in XMM0.  
```  
  
## <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Przykład 3 — wynik typu użytkownika przez wskaźnik wartości zwracanej  
  
```Output  
struct Struct1 {  
   int j, k, l;    // Struct1 exceeds 64 bits.   
};  
Struct1 func3(int a, double b, int c, float d);   
// Caller allocates memory for Struct1 returned and passes pointer in RCX,   
// a in RDX, b in XMM2, c in R9, d pushed on the stack;   
// callee returns pointer to Struct1 result in RAX.  
```  
  
## <a name="example-of-return-value-4---user-type-result-by-value"></a>Przykład zwracana wartość 4 - użytkownika typu wyniku przez wartość  
  
```Output  
struct Struct2 {  
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.  
};  
Struct2 func4(int a, double b, int c, float d);   
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;   
// callee returns Struct2 result by value in RAX.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)