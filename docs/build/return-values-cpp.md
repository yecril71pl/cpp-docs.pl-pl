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
ms.openlocfilehash: 673853417ad3dd5f08171ea2d5b55df5440705ad
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714640"
---
# <a name="return-values-c"></a>Wartości zwracane (C++)

Skalarne, zwracana wartość, którą można dopasować do 64 bitów jest zwracana za pośrednictwem RAX — w tym typy __m64. Typy non-scalar, w tym wartości zmiennoprzecinkowe wartości podwójnej precyzji i typy wektorowe, takie jak [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) są zwracane w XMM0. Stan nieużywane bity w wartości zwracanej w RAX lub XMM0 jest niezdefiniowane.

Typy zdefiniowane przez użytkownika mogą być zwracane przez wartość z funkcji globalnych i statycznych elementów członkowskich. Zwracane według wartości w RAX, typy zdefiniowane przez użytkownika musi mieć długość od 1, 2, 4, 8, 16, 32 lub 64-bitowy; nie zdefiniowane przez użytkownika Konstruktor, destruktor lub operator przypisania kopiowania; nie prywatnych lub chronionych niestatycznych składowych danych; nie elementów członkowskich danych niestatycznych typu odwołania; nie mają klas bazowych; żadnych funkcji wirtualnych; i żadnych składowych danych, które również nie spełniają tych wymagań. (To jest zasadniczo definicja C ++ 03 typu POD. Ponieważ definicja została zmieniona w standardem C ++ 11, nie zaleca się przy użyciu `std::is_pod` dla tego testu.) W przeciwnym razie obiekt wywołujący przejmie odpowiedzialność przydzielania pamięci i przekazywania wskaźnika dla wartości zwracanej jako pierwszy argument. Pozostałe argumenty są następnie przesunięte jeden argument w prawo. Ten sam wskaźnik muszą zostać zwrócony przez element wywołujący w RAX.

Poniższe przykłady pokazują sposób przekazywania parametrów i zwracanych wartości dla funkcji za pomocą określonego deklaracji:

## <a name="example-of-return-value-1---64-bit-result"></a>Przykład wartości zwracanej 1 – 64-bitowego wyniku

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

## <a name="example-of-return-value-2---128-bit-result"></a>Przykład wartości zwracanej 2-128-bitowego wyniku

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

## <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Przykład wartości zwracanej 3 – wynik typu użytkownika przez wskaźnik

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

## <a name="example-of-return-value-4---user-type-result-by-value"></a>Przykład wartości zwracanej 4 – wynik typu użytkownika według wartości

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