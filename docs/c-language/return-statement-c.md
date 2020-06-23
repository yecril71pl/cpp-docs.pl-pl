---
title: return — instrukcja (C)
description: Instrukcja return języka C przerywa wykonywanie funkcji i opcjonalnie zwraca wartość do obiektu wywołującego.
ms.date: 06/10/2020
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: 7d518aa17185c96de15c8f9aa9b65ae5c72bd014
ms.sourcegitcommit: 01b911613606c3fc92cbd9ca48cca6046a7e8258
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84716297"
---
# <a name="return-statement-c"></a>return — instrukcja (C)

**`return`** Instrukcja przerywa wykonywanie funkcji i zwraca sterowanie do funkcji wywołującej. Wykonanie wznowione w funkcji wywołującej w punkcie bezpośrednio po wywołaniu. **`return`** Instrukcja może zwracać wartość do wywołania funkcji. Aby uzyskać więcej informacji, zobacz [zwracany typ](../c-language/return-type.md).

## <a name="syntax"></a>Składnia

> *skoku-instrukcja*: \
> &nbsp;&nbsp;&nbsp;&nbsp;**`return`***wyrażenie*&#8203;<sub>wybór</sub>**`;`**

Wartość *wyrażenia*, jeśli jest obecna, jest zwracana do funkcji wywołującej. Jeśli *wyrażenie* zostanie pominięte, zwracana wartość funkcji jest niezdefiniowana. Wyrażenie, jeśli jest obecny, jest oceniane, a następnie konwertowane na typ zwracany przez funkcję. Gdy **`return`** instrukcja zawiera wyrażenie w funkcjach, które mają **`void`** zwracany typ, kompilator generuje ostrzeżenie i wyrażenie nie jest oceniane.

Jeśli **`return`** instrukcja nie pojawia się w definicji funkcji, formant automatycznie wraca do wywołania funkcji po wykonaniu ostatniej instrukcji wywołanej funkcji. W takim przypadku zwracana wartość wywoływanej funkcji jest niezdefiniowana. Jeśli funkcja ma zwracany typ inny niż **`void`** , jest to poważny błąd, a kompilator drukuje ostrzegawczy komunikat diagnostyczny. Jeśli funkcja ma **`void`** zwracany typ, to zachowanie jest odpowiednie, ale może być uznawane za słabego stylu. Użyj zwykłej **`return`** instrukcji, aby upewnić się, że intencja została wyczyszczona.

Dobrą metodą inżynieryjną jest zawsze określenie zwracanego typu dla funkcji. Jeśli zwracana wartość nie jest wymagana, należy zadeklarować funkcję jako **`void`** zwracanego typu. Jeśli zwracanym typem nie jest określony, kompilator C przyjmuje domyślny zwracany typ **`int`** .

Wielu programistów używa nawiasów, aby ująć argument *Expression* **`return`** instrukcji. Jednakże C nie wymaga nawiasów.

Kompilator może wydać ostrzeżenie komunikat diagnostyczny dotyczący nieosiągalnego kodu, jeśli odnajdzie wszystkie instrukcje umieszczone po **`return`** instrukcji.

W **`main`** funkcji **`return`** instrukcja i wyrażenie są opcjonalne. Co się stanie z wartością zwracaną, jeśli jest określona, zależy od implementacji. **Specyficzne dla firmy Microsoft**: implementacja języka Microsoft C zwraca wartość wyrażenia do procesu, który wywołał program, taki jak *`cmd.exe`* . Jeśli nie **`return`** podano wyrażenia, środowisko uruchomieniowe języka Microsoft C zwraca wartość wskazującą pomyślne (0) lub niepowodzenie (wartość niezerową).

## <a name="example"></a>Przykład

Ten przykład jest jednym programem w kilku częściach. Pokazuje on **`return`** instrukcję i sposób jej użycia zarówno do zakończenia wykonywania funkcji, jak i opcjonalnie, aby zwrócić wartość.

```C
// C_return_statement.c
// Compile using: cl /W4 C_return_statement.c
#include <limits.h>      // for INT_MAX
#include <stdio.h>       // for printf

long long square( int value )
{
    // Cast one operand to long long to force the
    // expression to be evaluated as type long long.
    // Note that parentheses around the return expression
    // are allowed, but not required here.
    return ( value * (long long) value );
}
```

`square`Funkcja zwraca kwadrat jego argumentu w szerszym typie, aby zapobiec błędzie arytmetycznym. **Specyficzne dla firmy Microsoft**: w implementacji języka Microsoft C **`long long`** Typ jest wystarczająco duży, aby pomieścić iloczyn dwóch **`int`** wartości bez przepełnienia.

Nawiasy wokół **`return`** wyrażenia w programie `square` są oceniane jako część wyrażenia i nie są wymagane przez **`return`** instrukcję.

```C
double ratio( int numerator, int denominator )
{
    // Cast one operand to double to force floating-point
    // division. Otherwise, integer division is used,
    // then the result is converted to the return type.
    return numerator / (double) denominator;
}
```

`ratio`Funkcja zwraca współczynnik dla dwóch **`int`** argumentów jako wartość zmiennoprzecinkową **`double`** . **`return`** Wyrażenie jest wymuszane do użycia operacji zmiennoprzecinkowej przez rzutowanie jednego z operandów na **`double`** . W przeciwnym razie zostanie użyty operator dzielenia liczby całkowitej, a część ułamkowa zostanie utracona.

```C
void report_square( void )
{
    int value = INT_MAX;
    long long squared = 0LL;
    squared = square( value );
    printf( "value = %d, squared = %lld\n", value, squared );
    return; // Use an empty expression to return void.
}
```

`report_square`Funkcja wywołuje `square` wartość parametru o `INT_MAX` największej wartości całkowitej ze znakiem, która mieści się w **`int`** . **`long long`** Wynik jest przechowywany w `squared` , a następnie wydrukowany. `report_square`Funkcja ma **`void`** zwracany typ, więc nie zawiera wyrażenia w **`return`** instrukcji.

```C
void report_ratio( int top, int bottom )
{
    double fraction = ratio( top, bottom );
    printf( "%d / %d = %.16f\n", top, bottom, fraction );
    // It's okay to have no return statement for functions
    // that have void return types.
}
```

`report_ratio`Funkcja wywołuje `ratio` wartości parametrów `1` i `INT_MAX` . **`double`** Wynik jest przechowywany w `fraction` , a następnie wydrukowany. `report_ratio`Funkcja ma **`void`** zwracany typ, więc nie musi jawnie zwracać wartości. Wykonanie operacji `report_ratio` "wypada w dół" i nie zwraca żadnej wartości do obiektu wywołującego.

```C
int main()
{
    int n = 1;
    int x = INT_MAX;

    report_square();
    report_ratio( n, x );

    return 0;
}
```

**`main`** Funkcja wywołuje dwie funkcje: `report_square` i `report_ratio` . Ponieważ nie `report_square` przyjmuje parametrów i zwraca **`void`** , nie przypiszemy jej wyniku do zmiennej. Podobnie `report_ratio` zwraca **`void`** , dlatego nie zapisujemy wartości zwracanej przez nas. Po każdym z tych wywołań funkcji wykonywanie jest kontynuowane przy następnej instrukcji. Następnie **`main`** zwraca wartość `0` (zazwyczaj używany do zgłaszania sukcesu), aby zakończyć program.

Aby skompilować przykład, Utwórz plik kodu źródłowego o nazwie *`C_return_statement.c`* . Następnie skopiuj cały przykładowy kod w podanej kolejności. Zapisz plik i skompiluj go w oknie wiersza polecenia dewelopera przy użyciu polecenia:

**`cl /W4 C_return_statement.c`**

Następnie, aby uruchomić przykładowy kod, wpisz **`C_return_statement.exe`** w wierszu polecenia. Dane wyjściowe przykładu wyglądają następująco:

```Output
value = 2147483647, squared = 4611686014132420609
1 / 2147483647 = 0.0000000004656613
```

## <a name="see-also"></a>Zobacz też

[Instrukcje](../c-language/statements-c.md)
