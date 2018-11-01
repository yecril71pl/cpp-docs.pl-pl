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
ms.openlocfilehash: f991eff82e5b6919f7960513ae9bc502cad77069
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641093"
---
# <a name="initializing-scalar-types"></a>Inicjowanie typów skalarnych

Podczas inicjowania skalarnych typów, wartości *wyrażenia przypisania* jest przypisany do zmiennej. Zastosuj reguły konwersji dla przypisania. (Zobacz [konwersje typów](../c-language/type-conversions-c.md) uzyskać informacji na temat reguł konwersji.)

## <a name="syntax"></a>Składnia

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *init-declarator-list*<sub>zoptymalizowany pod kątem</sub> **;**

*Specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub>

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list* **,** *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator* **=** *inicjatora*  / \* inicjowania skalarne \*/

*Inicjator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia przypisania*

Można zainicjować zmienne dowolnego typu, pod warunkiem, że należy przestrzegać następujących zasad:

- Zmienne zadeklarowane na poziomie zakresu pliku mogą być inicjowane. Jeśli nie jawnie zainicjować zmienną na poziomie zewnętrznym, domyślnie jest zainicjowany na 0.

- Wyrażenie stałe może służyć do zainicjowania dowolnej zmiennej globalnej zadeklarowane za pomocą **statyczne** *storage-class-specifier*. Zmienne zadeklarowane jako **statyczne** są inicjowane po rozpoczęciu wykonywania programu. Jeśli użytkownik nie jawnie zainicjować globalną **statyczne** zmiennej, jest on inicjowany 0 domyślnie, a każdy element członkowski, który ma typ wskaźnika jest przypisany wskaźnik zerowy.

- Zmienne zadeklarowane za pomocą **automatycznie** lub **zarejestrować** Specyfikator klasy magazynowania są zawsze zainicjowana podczas wykonywania kontrola przechodzi do bloku, w którym są one zgłoszone. Jeżeli pominięto inicjator po deklaracji **automatycznie** lub **zarejestrować** zmiennej, początkowa wartość zmiennej jest niezdefiniowana. Aby uzyskać automatyczne i wartości rejestru, Inicjator nie jest ograniczony do bycia stałą; może być dowolne wyrażenie obejmujące wartości uprzednio zdefiniowany, wywołania funkcji nawet.

- Deklaracje zmiennych zewnętrznych i dla wszystkich wartości początkowe **statyczne** zmiennych zewnętrznych lub wewnętrznych, muszą być wyrażeniami stałymi. (Aby uzyskać więcej informacji, zobacz [wyrażeń stałych](../c-language/c-constant-expressions.md).) Ponieważ adres wszystkie zewnętrznie zadeklarowana lub statycznej zmiennej jest stała, może służyć do zainicjowania wewnętrznie zadeklarowane **statyczne** zmiennej wskaźnika. Jednak adres **automatycznie** zmiennej nie można użyć jako statycznego inicjatora, ponieważ mogą być różne dla każdego wykonania bloku. Aby zainicjować można użyć wartości stałych czy zmiennych **automatycznie** i **zarejestrować** zmiennych.

- Jeśli deklaracja identyfikator ma zakres bloku, a identyfikator ma powiązania zewnętrzne, deklaracja nie może mieć inicjalizacji.

## <a name="examples"></a>Przykłady

Poniższe przykłady ilustrują, inicjalizacje:

```C
int x = 10;
```

Zmienna liczba całkowita `x` jest inicjowany do stałego wyrażenia `10`.

```C
register int *px = 0;
```

Wskaźnik `px` jest inicjowana wartością 0, tworzenie wskaźnika "o wartości null".

```C
const int c = (3 * 1024);
```

W tym przykładzie użyto wyrażenia stałego `(3 * 1024)` zainicjować `c` wartość stałą, którego nie można zmodyfikować z powodu **const** — słowo kluczowe.

```C
int *b = &x;
```

Ta instrukcja inicjuje wskaźnik `b` przy użyciu adresu innej zmiennej `x`.

```C
int *const a = &z;
```

Wskaźnik `a` jest inicjowany za pomocą adresu zmiennej o nazwie `z`. Jednakże, ponieważ jest określony jako **const**, zmienna `a` może być inicjowane tylko, nigdy modyfikowany. Zawsze wskazuje w tej samej lokalizacji.

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

Zmienna globalna `GLOBAL` zadeklarowane na poziomie zewnętrznym, dlatego ma globalny okres istnienia. Zmienna lokalna `LOCAL` ma **automatycznie** klasę magazynu i adres jest tylko podczas wykonywania funkcji, w którym jest zdeklarowana. W związku z tym, podejmuje próbę zainicjowania **statyczne** zmiennej wskaźnikowej `lp` adresem `LOCAL` nie jest dozwolone. **Statyczne** zmiennej wskaźnikowej `gp` mogą być inicjowane jako adres `GLOBAL` ponieważ ten adres jest zawsze taki sam. Podobnie `*rp` mogą być zainicjowane, ponieważ `rp` jest zmienną lokalną i może mieć inicjatora stałymi. Każdorazowo po wprowadzeniu bloku `LOCAL` ma nowego adresu, który jest przypisywany do `rp`.

## <a name="see-also"></a>Zobacz też

[Inicjowanie](../c-language/initialization.md)