---
title: __assume
ms.date: 09/02/2019
f1_keywords:
- __assume
- _assume
- __assume_cpp
helpviewer_keywords:
- __assume keyword [C++]
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
ms.openlocfilehash: f3f847b5268605bdc5df90a8bbc6a88c78431864
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216961"
---
# <a name="__assume"></a>__assume

**Microsoft Specific**

Przekazuje wskazówkę do Optymalizatora.

## <a name="syntax"></a>Składnia

```C
__assume(
   expression
)
```

### <a name="parameters"></a>Parametry

*wyrażenia*\
Dowolne wyrażenie, które ma zostać obliczone na wartość true.

## <a name="remarks"></a>Uwagi

Optymalizator zakłada, że warunek reprezentowany przez `expression` ma wartość true w punkcie, w którym słowo kluczowe pojawia się i pozostaje prawdziwe do czasu `expression` modyfikacji (na przykład przez przypisanie do zmiennej). Wybiórcze użycie wskazówek przekazanie do Optymalizatora przez `__assume` program może poprawić optymalizację.

Jeśli instrukcja jest zapisywana jako sprzeczność (wyrażenie, które zawsze ma wartość false), jest zawsze traktowane jako `__assume(0)`. `__assume` Jeśli kod nie zachowuje się zgodnie z `expression` oczekiwaniami, upewnij się, że zdefiniowany jest prawidłowy i prawdziwy, zgodnie z wcześniejszym opisem. Aby uzyskać więcej informacji na `__assume(0)` temat oczekiwanego zachowania, zobacz późniejsze uwagi.

> [!WARNING]
>  Program nie może zawierać nieprawidłowej `__assume` instrukcji w dostępnej ścieżce. Jeśli kompilator może dotrzeć do nieprawidłowej `__assume` instrukcji, program może spowodować nieprzewidywalne i potencjalnie niebezpieczne zachowanie.

`__assume`nie jest oryginalnym elementem wewnętrznym. Nie musi być zadeklarowana jako funkcja i nie może być używana w `#pragma intrinsic` dyrektywie. Chociaż żaden kod nie jest generowany, ma to wpływ na kod wygenerowany przez optymalizator.

Użyj `__assume` w potwierdzeniu tylko wtedy, gdy potwierdzenie nie jest możliwe do odzyskania. [](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) Nie należy używać `__assume` w potwierdzeniu, dla którego kod odzyskiwania został zwrócony, ponieważ kompilator może zoptymalizować kod obsługi błędu.

`__assume(0)` Instrukcja jest szczególnym przypadkiem. Użyj `__assume(0)` , aby wskazać ścieżkę kodu, której nie można osiągnąć. Poniższy przykład pokazuje, jak używać `__assume(0)` do wskazania, że nie można osiągnąć domyślnego przypadku instrukcji switch. Jest to najbardziej typowe użycie `__assume(0)`.

Aby zapewnić zgodność z poprzednimi wersjami, **_assume** jest synonimem dla **__assume** , chyba że jest określona opcja kompilatora [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__assume`|x86, ARM, x64, ARM64|

## <a name="example"></a>Przykład

```cpp
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

Użycie `__assume(0)` informuje optymalizator, że nie można osiągnąć domyślnego przypadku. Przykład pokazuje, że programista wie, że jedynymi możliwymi `p` danymi wejściowymi będzie 1 lub 2. Jeśli inna wartość jest przenoszona do `p`programu, program jest nieprawidłowy i powoduje nieprzewidywalne zachowanie.

W wyniku `__assume(0)` instrukcji kompilator nie generuje kodu w celu przetestowania, czy `p` ma wartość, która nie jest reprezentowana w instrukcji case. Aby to działało, `__assume(0)` instrukcja musi być pierwszą instrukcją w treści domyślnego przypadku.

Ponieważ kompilator generuje kod na podstawie `__assume`, kod może nie działać poprawnie, jeśli wyrażenie `__assume` wewnątrz instrukcji ma wartość FAŁSZ w czasie wykonywania. Jeśli nie masz pewności, że wyrażenie będzie zawsze prawdziwe w czasie wykonywania, możesz użyć `assert` funkcji, aby chronić kod.

```C
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )
```

Niestety, to użycie `assert` uniemożliwi kompilatorowi wykonywanie optymalizacji przypadku domyślnego, która została opisana wcześniej w tym dokumencie. Alternatywnie można użyć oddzielnego makra w następujący sposób.

```C
#ifdef DEBUG
# define NODEFAULT   ASSERT(0)
#else
# define NODEFAULT   __assume(0)
#endif

   default:
      NODEFAULT;
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
