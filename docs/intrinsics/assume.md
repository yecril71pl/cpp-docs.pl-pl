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
ms.openlocfilehash: 06189405703a7cc34f3bd807ec79612394ee899f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368199"
---
# <a name="__assume"></a>__assume

**Specyficzne dla firmy Microsoft**

Przekazuje wskazówkę do optymalizatora.

## <a name="syntax"></a>Składnia

```C
__assume(
   expression
)
```

### <a name="parameters"></a>Parametry

*Wyrażenie*\
Każde wyrażenie, które jest zakładane do oceny true.

## <a name="remarks"></a>Uwagi

Optymalizator zakłada, że warunek `expression` reprezentowany przez jest true w punkcie, `expression` w którym pojawia się słowo kluczowe i pozostaje true, dopóki nie zostanie zmodyfikowany (na przykład przez przypisanie do zmiennej). Selektywne stosowanie wskazówek przekazywanych `__assume` do optymalizatora przez może poprawić optymalizację.

Jeśli `__assume` instrukcja jest napisana jako sprzeczność (wyrażenie, które zawsze ocenia jako `__assume(0)`fałszywe), jest zawsze traktowana jako . Jeśli kod nie zachowuje się zgodnie z `expression` oczekiwaniami, upewnij się, że zdefiniowane jest prawidłowe i prawdziwe, jak opisano wcześniej. Aby uzyskać więcej `__assume(0)` informacji na temat oczekiwanego zachowania, zobacz późniejsze uwagi.

> [!WARNING]
> Program nie może zawierać `__assume` nieprawidłowej instrukcji na dostępnej ścieżce. Jeśli kompilator może `__assume` osiągnąć nieprawidłową instrukcję, program może spowodować nieprzewidywalne i potencjalnie niebezpieczne zachowanie.

`__assume`nie jest prawdziwym wewnętrzną. Nie musi być zadeklarowany jako funkcja i nie `#pragma intrinsic` może być stosowany w dyrektywie. Mimo że nie jest generowany kod, kod generowany przez optymalizator ma wpływ.

Użyj `__assume` w [ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) tylko wtedy, gdy potwierdzenia nie jest możliwe do odzyskania. Nie należy `__assume` używać w assert, dla którego masz kolejny kod odzyskiwania błędów, ponieważ kompilator może zoptymalizować od kodu obsługi błędów.

Oświadczenie `__assume(0)` jest szczególnym przypadkiem. Służy `__assume(0)` do wskazywania ścieżki kodu, do której nie można osiągnąć. W poniższym przykładzie `__assume(0)` pokazano, jak użyć, aby wskazać, że nie można osiągnąć domyślnego przypadku instrukcji switch. Pokazuje to najbardziej typowe `__assume(0)`zastosowanie .

W przypadku zgodności z poprzednimi wersjami **_assume** jest synonimem **__assume** chyba że określono opcję kompilatora [/Za \(Wyłącz rozszerzenia języka).](../build/reference/za-ze-disable-language-extensions.md)

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
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

Użycie optymalizatora `__assume(0)` informuje, że nie można osiągnąć domyślnego przypadku. Przykład pokazuje, że programista wie, że tylko `p` możliwe dane wejściowe dla będzie 1 lub 2. Jeśli inna wartość jest `p`przekazywana dla programu, program staje się nieprawidłowy i powoduje nieprzewidywalne zachowanie.

W wyniku `__assume(0)` instrukcji kompilator nie generuje kodu, `p` aby sprawdzić, czy ma wartość, która nie jest reprezentowana w case statement. Aby to działało, instrukcja `__assume(0)` musi być pierwszą instrukcją w treści domyślnej sprawy.

Ponieważ kompilator generuje kod `__assume`na podstawie , że kod może `__assume` nie działać poprawnie, jeśli wyrażenie wewnątrz instrukcji jest false w czasie wykonywania. Jeśli nie masz pewności, że wyrażenie będzie zawsze true w `assert` czasie wykonywania, można użyć funkcji do ochrony kodu.

```C
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )
```

Niestety to użycie `assert` uniemożliwia kompilatorowi wykonywanie optymalizacji przypadków domyślnych, który został opisany wcześniej w tym dokumencie. Alternatywnie można użyć oddzielnego makra w następujący sposób.

```C
#ifdef DEBUG
# define NODEFAULT   ASSERT(0)
#else
# define NODEFAULT   __assume(0)
#endif

   default:
      NODEFAULT;
```

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Wewnętrzne właściwości kompilatora](../intrinsics/compiler-intrinsics.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
