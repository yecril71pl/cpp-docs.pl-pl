---
title: Inicjowanie typów skalarnych
ms.date: 11/04/2016
helpviewer_keywords:
- initializing scalar types
- register variables
- initialization, scalar types
- initializing variables, scalar types
- scalar types
- static variables, initializing
- automatic storage class, initializing scalar types
- automatic storage class
- types [C], initializing
ms.assetid: 73c516f5-c3ad-4d56-ab3b-f2a82b621104
ms.openlocfilehash: 063761abcbb1541893b9cbab463e3d121684d00a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211830"
---
# <a name="initializing-scalar-types"></a>Inicjowanie typów skalarnych

Podczas inicjowania typów skalarnych wartość *`assignment-expression`* jest przypisana do zmiennej. Reguły konwersji dla przypisania mają zastosowanie. (Zobacz [konwersje typów](../c-language/type-conversions-c.md) , aby uzyskać informacje o regułach konwersji).

## <a name="syntax"></a>Składnia

*`declaration`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`**`init-declarator-list`* <sub>wybór</sub>**`;`**

*`declaration-specifiers`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`storage-class-specifier`**`declaration-specifiers`* <sub>wybór</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-specifier`**`declaration-specifiers`* <sub>wybór</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-qualifier`**`declaration-specifiers`* <sub>wybór</sub>

*`init-declarator-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator-list`* **`,`** *`init-declarator`*

*`init-declarator`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`***`=`** *`initializer`* /\* Na potrzeby inicjacji skalarnej\*/

*`initializer`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`assignment-expression`*

Można inicjować zmienne dowolnego typu, pod warunkiem przestrzegania następujących zasad:

- Zmienne zadeklarowane na poziomie plików mogą być inicjowane. Jeśli zmienna nie zostanie jawnie zainicjowana na poziomie zewnętrznym, domyślnie jest inicjowana wartość 0.

- Wyrażenie stałe może służyć do inicjowania dowolnej zmiennej globalnej zadeklarowanej za pomocą **`static`** *`storage-class-specifier`* . Zmienne zadeklarowane jako **`static`** są inicjowane po rozpoczęciu wykonywania programu. Jeśli nie zainicjujesz jawnie zmiennej globalnej **`static`** , zostanie ona domyślnie zainicjowana przez 0, a każdy element członkowski, który ma typ wskaźnika, ma przypisany wskaźnik o wartości null.

- Zmienne zadeklarowane ze **`auto`** **`register`** specyfikatorem klasy magazynu lub są inicjowane za każdym razem, gdy Sterowanie wykonywaniem przechodzi do bloku, w którym są one zadeklarowane. Jeśli pominięto inicjator z deklaracji **`auto`** **`register`** zmiennej lub, początkowa wartość zmiennej jest niezdefiniowana. W przypadku wartości automatycznych i rejestr inicjator nie jest ograniczony do stałej; może to być dowolne wyrażenie obejmujące poprzednio zdefiniowane wartości, nawet wywołania funkcji.

- Początkowe wartości dla deklaracji zmiennych zewnętrznych i dla wszystkich **`static`** zmiennych, bez względu na to, czy zewnętrzne, czy wewnętrzne, muszą być wyrażeniami stałymi. (Aby uzyskać więcej informacji, zobacz [wyrażenia stałe](../c-language/c-constant-expressions.md)). Ponieważ adres każdej zmiennej zadeklarowanej zewnętrznie lub zmienna statyczna jest stała, może służyć do inicjowania wewnętrznie zadeklarowanej **`static`** zmiennej wskaźnika. Jednak adres **`auto`** zmiennej nie może być używany jako inicjator statyczny, ponieważ może być inny dla każdego wykonywania bloku. Można użyć wartości stałych lub zmiennych, aby inicjować **`auto`** i **`register`** zmienne.

- Jeśli deklaracja identyfikatora ma zakres bloku, a identyfikator ma powiązania zewnętrzne, deklaracja nie może mieć inicjalizacji.

## <a name="examples"></a>Przykłady

Następujące przykłady ilustrują inicjalizacje:

```C
int x = 10;
```

Zmienna typu Integer `x` została zainicjowana w wyrażeniu stałym `10` .

```C
register int *px = 0;
```

Wskaźnik `px` jest zainicjowany do 0, generując wskaźnik "null".

```C
const int c = (3 * 1024);
```

W tym przykładzie używane jest wyrażenie stałe `(3 * 1024)` do zainicjowania `c` do stałej wartości, której nie można zmodyfikować ze względu na **`const`** słowo kluczowe.

```C
int *b = &x;
```

Ta instrukcja inicjuje wskaźnik `b` z adresem innej zmiennej, `x` .

```C
int *const a = &z;
```

Wskaźnik `a` zostanie zainicjowany przy użyciu adresu zmiennej o nazwie `z` . Jednak ponieważ jest określony jako **`const`** , zmienna `a` może zostać zainicjowana, nigdy nie modyfikowana. Zawsze wskazuje tę samą lokalizację.

```C
int GLOBAL ;

int function( void )
{
    int LOCAL ;
    static int *lp = &LOCAL;   /* Illegal initialization */
    static int *gp = &GLOBAL;  /* Legal initialization   */
    register int *rp = &LOCAL; /* Legal initialization   */
}
```

Zmienna globalna `GLOBAL` jest zadeklarowana na poziomie zewnętrznym, więc ma globalny okres istnienia. Zmienna lokalna `LOCAL` ma **`auto`** klasę magazynu i ma tylko adres podczas wykonywania funkcji, w której jest zadeklarowana. W związku z tym próba zainicjowania **`static`** zmiennej wskaźnika `lp` o adresie `LOCAL` jest niedozwolona. **`static`** Zmienna wskaźnikowa `gp` może zostać zainicjowana na adres, `GLOBAL` ponieważ ten adres jest zawsze taki sam. Podobnie, `*rp` można zainicjować, ponieważ `rp` jest zmienną lokalną i może mieć inicjator niestały. Za każdym razem, gdy zostanie wprowadzony blok, `LOCAL` ma nowy adres, który następnie jest przypisany do `rp` .

## <a name="see-also"></a>Zobacz także

[Inicjalizacja](../c-language/initialization.md)
