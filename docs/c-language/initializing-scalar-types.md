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
ms.openlocfilehash: 3cf7eddcf43a65a787de60c391863d6471be7bcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232946"
---
# <a name="initializing-scalar-types"></a>Inicjowanie typów skalarnych

Podczas inicjowania typów skalarnych wartość *wyrażenia przypisania* jest przypisana do zmiennej. Reguły konwersji dla przypisania mają zastosowanie. (Zobacz [konwersje typów](../c-language/type-conversions-c.md) , aby uzyskać informacje o regułach konwersji).

## <a name="syntax"></a>Składnia

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracje-specyfikatory* *init-deklarator-list*<sub>opt</sub> **;**

*specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja* *specyfikatora klasy magazynu* —<sub>wybór</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *specyfikatora typu* *— wybór specyfikatorów*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *kwalifikatora typu* *— wybór specyfikatorów*<sub>opt</sub>

*init-deklarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator-list* **,** *init-deklarator*

*init-deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *initializer* inicjator / deklarator dla inicjalizacji skalarnej\*\*/

*inicjator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przypisanie — wyrażenie*

Można inicjować zmienne dowolnego typu, pod warunkiem przestrzegania następujących zasad:

- Zmienne zadeklarowane na poziomie plików mogą być inicjowane. Jeśli zmienna nie zostanie jawnie zainicjowana na poziomie zewnętrznym, domyślnie jest inicjowana wartość 0.

- Wyrażenie stałe może służyć do inicjowania dowolnej zmiennej globalnej zadeklarowanej ze *specyfikatorem klasy magazynu* **static** . Zmienne zadeklarowane jako **statyczne** są inicjowane po rozpoczęciu wykonywania programu. Jeśli nie zainicjujesz jawnie globalnej zmiennej **statycznej** , zostanie ona domyślnie zainicjowana przez 0, a każdy element członkowski, który ma typ wskaźnika, ma przypisany wskaźnik o wartości null.

- Zmienne zadeklarowane za pomocą specyfikatora klasy magazynu autolub **rejestru** są inicjowane za każdym **razem, gdy** kontrola wykonywania przechodzi do bloku, w którym są one zadeklarowane. Jeśli pominięto inicjator z deklaracji zmiennej **autolub** **register** , początkowa wartość zmiennej jest niezdefiniowana. W przypadku wartości automatycznych i rejestr inicjator nie jest ograniczony do stałej; może to być dowolne wyrażenie obejmujące poprzednio zdefiniowane wartości, nawet wywołania funkcji.

- Początkowe wartości dla deklaracji zmiennych zewnętrznych i dla wszystkich zmiennych **statycznych** , bez względu na to, czy zewnętrzne, czy wewnętrzne, muszą być wyrażeniami stałymi. (Aby uzyskać więcej informacji, zobacz [wyrażenia stałe](../c-language/c-constant-expressions.md)). Ponieważ adres każdej zmiennej zadeklarowanej zewnętrznie lub zmienna statyczna jest stała, można go użyć do zainicjowania wewnętrznie zadeklarowanej zmiennej wskaźnik **statyczny** . Jednak **adres zmiennej** autovariable nie może być używany jako inicjator statyczny, ponieważ może być inny dla każdego wykonywania bloku. Można użyć wartości stałych lub zmiennych, **aby inicjować zmienne** autoi **rejestrujące** .

- Jeśli deklaracja identyfikatora ma zakres bloku, a identyfikator ma powiązania zewnętrzne, deklaracja nie może mieć inicjalizacji.

## <a name="examples"></a>Przykłady

Następujące przykłady ilustrują inicjalizacje:

```C
int x = 10;
```

Zmienna `x` typu Integer została zainicjowana w wyrażeniu `10`stałym.

```C
register int *px = 0;
```

Wskaźnik `px` jest zainicjowany do 0, generując wskaźnik "null".

```C
const int c = (3 * 1024);
```

W tym przykładzie używane jest wyrażenie `(3 * 1024)` stałe do `c` zainicjowania do stałej wartości, której nie można zmodyfikować ze względu na słowo kluczowe **const** .

```C
int *b = &x;
```

Ta instrukcja inicjuje wskaźnik `b` z adresem innej zmiennej,. `x`

```C
int *const a = &z;
```

Wskaźnik `a` zostanie zainicjowany przy użyciu adresu zmiennej o nazwie `z`. Jednak ponieważ jest określony jako **const**, zmienna `a` może zostać zainicjowana, nigdy nie modyfikowana. Zawsze wskazuje tę samą lokalizację.

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

Zmienna `GLOBAL` globalna jest zadeklarowana na poziomie zewnętrznym, więc ma globalny okres istnienia. Zmienna `LOCAL` lokalna ma klasę **autostorage i ma tylko** adres podczas wykonywania funkcji, w której jest zadeklarowana. W związku z tym próba zainicjowania zmiennej `lp` wskaźnika **statycznego** o adresie `LOCAL` jest niedozwolona. Zmienna `gp` wskaźnik **statyczna** może zostać zainicjowana na adres `GLOBAL` , ponieważ ten adres jest zawsze taki sam. Podobnie można `*rp` zainicjować, ponieważ `rp` jest to zmienna lokalna i może mieć inicjator niestały. Za każdym razem, gdy zostanie wprowadzony `LOCAL` blok, ma nowy adres, który następnie jest przypisany `rp`do.

## <a name="see-also"></a>Zobacz też

[Inicjowanie](../c-language/initialization.md)
