---
title: __assume | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __assume
- __assume_cpp
dev_langs:
- C++
helpviewer_keywords:
- __assume keyword [C++]
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1c8c37bc46580db42bfa2a91d215b09bc1dbaf4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405700"
---
# <a name="assume"></a>__assume

**Microsoft Specific**

Przekazuje podpowiedź optymalizatora.

## <a name="syntax"></a>Składnia

```
__assume(
   expression
)
```

#### <a name="parameters"></a>Parametry

*Wyrażenie*<br/>
Dowolne wyrażenie, które jest zakłada się, że zostało oszacowane jako prawdziwe.

## <a name="remarks"></a>Uwagi

Optymalizator przyjęto założenie, że warunek jest reprezentowana przez `expression` ma wartość true w punkcie, w których słowa kluczowego pojawia się i pozostaje prawdziwy aż do `expression` zostanie zmodyfikowany (np. przez przypisanie do zmiennej). Selektywne stosowanie wskazówek przekazany do optymalizacji przez `__assume` może zwiększyć optymalizacji.

Jeśli `__assume` instrukcji jest zapisywany jako sprzeczne (wyrażenie, które zawsze zwróci wartość false), jest on zawsze traktowany `__assume(0)`. Jeśli Twój kod niezgodnie z oczekiwaniami, upewnij się, że `expression` zdefiniowany jest prawidłowy i ma wartość true, zgodnie z wcześniejszym opisem. Aby uzyskać więcej informacji na temat Oczekiwano `__assume(0)` zachowania, zobacz sekcję Uwagi w późniejszym.

> [!WARNING]
>  Program nie może zawierać nieprawidłową `__assume` instrukcji w ścieżce osiągalny. Jeśli kompilator może dotrzeć nieprawidłową `__assume` instrukcji, program może spowodować nieprzewidywalne i potencjalnie niebezpieczne zachowania.

`__assume` nie jest oryginalne wewnętrzne. Nie musi być zadeklarowana jako funkcja i nie można używać w `#pragma intrinsic` dyrektywy. Mimo że nie wygenerowano żadnego kodu, kod wygenerowany przez optymalizator ma wpływ.

Użyj `__assume` w [ASERCJA](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) tylko wtedy, gdy asercja nie jest możliwe do odzyskania. Nie używaj `__assume` w assert, do której masz kod odzyskiwania kolejny błąd, ponieważ kompilator może optymalizują kodu obsługi błędu.

`__assume(0)` Instrukcji jest przypadkiem szczególnym. Użyj `__assume(0)` do wskazania ścieżka kodu, która nie można nawiązać połączenia. Poniższy przykład pokazuje, jak używać `__assume(0)` do wskazania, że przypadek domyślny instrukcji switch nie można nawiązać połączenia. Pokazuje to najbardziej typowy użytkowania `__assume(0)`.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__assume`|x86, ARM, x64|

## <a name="example"></a>Przykład

```
// compiler_intrinsics__assume.cpp
#ifdef DEBUG
# define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__) )
#else
# define ASSERT(e)    ( __assume(e) )
#endif

void func1(int i)
{
}

int main(int p)
{
   switch(p){
      case 1:
         func1(1);
         break;
      case 2:
         func1(-1);
         break;
      default:
         __assume(0);
            // This tells the optimizer that the default
            // cannot be reached. As so, it does not have to generate
            // the extra code to check that 'p' has a value
            // not represented by a case arm. This makes the switch
            // run faster.
   }
}
```

Korzystanie z `__assume(0)` Optymalizator informuje, że przypadek domyślny nie można nawiązać połączenia. W przykładzie pokazano programistę wie, że tylko to możliwe, danych wejściowych dla `p` będzie 1 lub 2. Jeśli inna wartość jest przekazywana do `p`, program staje się nieprawidłowy i powoduje, że nieprzewidywalne zachowanie.

Na `__assume(0)` instrukcji, kompilator nie generuje kodu, aby przetestować czy `p` ma wartość, która nie jest reprezentowana w instrukcji case. Aby to działało `__assume(0)` instrukcja musi być pierwszą instrukcją w treści przypadek domyślny.

Ponieważ kompilator generuje kod na podstawie `__assume`, ten kod może nie działać poprawnie, jeśli wyrażenie wewnątrz `__assume` instrukcji ma wartość false w czasie wykonywania. Jeśli nie masz pewności, że wyrażenie będzie zawsze wartość true w czasie wykonywania, możesz użyć `assert` funkcję, aby zabezpieczyć ten kod.

```
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )
```

Niestety, to użycie `assert` zabezpiecza kompilator przed wykonaniem optymalizacji przypadek domyślny, który został opisany wcześniej w tym dokumencie. Alternatywnie można użyć oddzielnych makra, w następujący sposób.

```
#ifdef DEBUG
# define NODEFAULT   ASSERT(0)
#else
# define NODEFAULT   __assume(0)
#endif

   default:
      NODEFAULT;
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)