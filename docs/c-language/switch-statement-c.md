---
title: switch — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- switch
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
ms.openlocfilehash: 0f781147bf4ed020cf925ca29c2ba1b0f601cde1
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148195"
---
# <a name="switch-statement-c"></a>switch — instrukcja (C)

`switch` i **przypadek** instrukcji pomocy złożonych warunkowe i rozgałęzień operacje kontroli. `switch` Instrukcji przekazuje sterowanie do instrukcji w swojej treści.

## <a name="syntax"></a>Składnia

*Wybór instrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przełącz (** *wyrażenie* **)** *— instrukcja*

*labeled-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**przypadek** *wyrażenie_stałe* **:** *— instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**domyślne:** *— instrukcja*

Kontrola przechodzi do instrukcji, których **przypadek** *wyrażenie_stałe* odpowiada wartości **przełącznika (** *wyrażenie* **)**. `switch` Instrukcji może zawierać dowolną liczbę **przypadek** wystąpień, ale nie dwie stałe wielkości liter, w tym samym `switch` instrukcja może mieć taką samą wartość. Wykonanie treści instrukcji rozpoczyna się od wybranej instrukcji i jest kontynuowane do czasu zakończenia treści lub do momentu **podziału** instrukcji przenosi sterowanie na zewnątrz treści.

Korzystanie z `switch` instrukcji zwykle wygląda następująco:

```C
switch ( expression )
{
    // declarations
    // . . .
    case constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        break;
    default:
        // statements executed if expression does not equal
        // any case constant_expression
}
```

Możesz użyć **podziału** instrukcję, aby zakończyć przetwarzanie określonego wielkość liter w obrębie `switch` instrukcji i gałęzi do końca `switch` instrukcji. Bez **podziału**, program przechodzi do następnego wystąpienia case wykonywania instrukcji do momentu **podziału** lub osiągnięty zostanie koniec instrukcji. W niektórych sytuacjach może być pożądane kontynuacji.

**Domyślne** instrukcja jest wykonywana, jeśli nie **przypadek** *wyrażenie_stałe* jest równa wartości **przełącznika (**  *wyrażenie* **)**. Jeśli **domyślne** instrukcji zostanie pominięty i nie **przypadek** zostanie znalezione dopasowanie, żadna z instrukcji w `switch` treści są wykonywane. Może być co najwyżej jeden **domyślne** instrukcji. **Domyślne** deklaracja nie musi pojawić się na końcu; może występować dowolnym miejscu w treści `switch` instrukcji. A **przypadek** lub **domyślne** etykieta może wystąpić tylko wewnątrz `switch` instrukcji.

Typ `switch` *wyrażenie* i **przypadek** *wyrażenie_stałe* musi być typu całkowitego. Wartość każdego **przypadek** *wyrażenie_stałe* muszą być unikatowe w treści instrukcji.

**Przypadek** i **domyślne** etykiety `switch` treść instrukcji są istotne tylko w przypadku testu wstępnego, który określa, gdzie się rozpoczyna wykonywanie w treści instrukcji. Można zagnieździć instrukcji Switch. Wszystkie statyczne zmienne są inicjowane przed wykonaniem w każdym `switch` instrukcji.

> [!NOTE]
> Deklaracje może znajdować się na czele tworzących instrukcji złożonej `switch` treści, ale inicjalizacje zawarte w deklaracji nie są wykonywane. `switch` Instrukcji przekazuje sterowanie bezpośrednio do instrukcji wykonywalnej w treści, z pominięciem wierszy, które zawierają inicjalizacji.

Poniższe przykłady ilustrują `switch` instrukcji:

```C
switch( c )
{
    case 'A':
        capa++;
    case 'a':
        lettera++;
    default :
        total++;
}
```

Wszystkie trzy instrukcje `switch` treści, w tym przykładzie są wykonywane, jeśli `c` jest równa `'A'` ponieważ **podziału** przed następujący przypadek nie ma instrukcji. Wykonanie kontrola jest przekazywana do pierwszej instrukcji (`capa++;`) i jest kontynuowane w kolejności przez pozostałą część treści. Jeśli `c` jest równa `'a'`, `lettera` i `total` są zwiększane. Tylko `total` jest zwiększana, gdy `c` nie jest równa `'A'` lub `'a'`.

```C
switch( i )
{
    case -1:
        n++;
        break;
    case 0 :
        z++;
        break;
    case 1 :
        p++;
        break;
}
```

W tym przykładzie **podziału** instrukcji, następuje po każdej instrukcji z `switch` treści. **Podziału** instrukcji wymusza wyjście z treści instrukcji po wykonaniu jednej instrukcji. Jeśli `i` jest równy -1, tylko `n` jest zwiększany. **Podziału** następującej po instrukcji `n++;` powoduje, że kontrola wykonywania do przekazania poza treści instrukcji z pominięciem pozostałe instrukcje. Podobnie jeśli `i` jest równa 0, tylko `z` jest zwiększany; Jeśli `i` jest równa 1, tylko `p` jest zwiększany. Końcowe **podziału** instrukcja nie jest to niezbędne, ponieważ kontrola przechodzi z treści na końcu instrukcji złożonej, ale jest uwzględniony w celu zachowania spójności.

Pojedynczej instrukcji może wykonywać wiele **przypadek** etykiet, jak w poniższym przykładzie pokazano:

```C
case 'a' :
case 'b' :
case 'c' :
case 'd' :
case 'e' :
case 'f' :  hexcvt(c);
```

W tym przykładzie Jeśli *wyrażenie_stałe* jest równa dowolnej litery między `'a'` i `'f'`, `hexcvt` funkcja jest wywoływana.

**Microsoft Specific**

Microsoft C nie ogranicza liczby przypadków wartości w `switch` instrukcji. Liczba jest ograniczona jedynie ilością dostępnej pamięci. ANSI C wymaga co najmniej 257 etykiet wielkości liter jest dozwolone w `switch` instrukcji.

Wartość domyślna Microsoft C to, że są włączone rozszerzenia Microsoft. Aby wyłączyć te rozszerzenia, należy użyć /Za — opcja kompilatora.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[switch, instrukcja (C++)](../cpp/switch-statement-cpp.md)
