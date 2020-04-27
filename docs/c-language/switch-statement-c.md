---
title: switchInstrukcja (C)
ms.date: 04/25/2020
f1_keywords:
- switch
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- switch
- case
- default
- break
ms.openlocfilehash: 12163e85110092e3e372fa496cf42efd7574ea8d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167679"
---
# <a name="opno-locswitch-statement-c"></a>switchInstrukcja (C)

Instrukcje **switch** i **case** ułatwiają kontrolę złożonych operacji warunkowych i rozgałęzień. **switch** Instrukcja przekazuje formant do instrukcji w jej treści.

## <a name="syntax"></a>Składnia

*wybór — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`switch (`***expression* **`)`** *instrukcja* wyrażenia

*etykieta — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`case`**  *stała —***`:`***instrukcja* wyrażenia    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`default :`**  *Merge*

Kontrolka przechodzi do instrukcji, **case** *wyrażenie stałe* dopasowuje wartość ** switch (** *wyrażenie* **)**. **switch** Instrukcja może zawierać dowolną liczbę **case** wystąpień. Jednak żadne dwie case stałe w tej samej **switch** instrukcji nie mogą mieć tej samej wartości. Wykonywanie treści instrukcji rozpoczyna się od wybranej instrukcji. Przechodzi do końca treści lub do momentu, aż **break** instrukcja przeniesie kontrolę z treści.

Użycie **switch** instrukcji zwykle wygląda następująco:

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

Możesz użyć instrukcji, **break** aby zakończyć przetwarzanie konkretnej instrukcji oznaczonej etykietą w **switch** instrukcji. Oddziały IT do końca **switch** instrukcji. Bez **break**, program przechodzi do następnej instrukcji oznaczonej etykietą, wykonując instrukcje do momentu osiągnięcia **break** lub zakończenia instrukcji. Kontynuacja może być pożądana w niektórych sytuacjach.

Instrukcja **default** jest wykonywana, jeśli żadne **case** *wyrażenie stałe* nie jest równe wartości ** switch (** *wyrażenie* **)**. Jeśli nie ma żadnej **default** instrukcji i nie **case** znaleziono dopasowania, żadna z instrukcji w **switch** treści nie zostanie wykonana. Może istnieć co najwyżej jedna **default** instrukcja. **default** Instrukcja nie musi znajdować się na końcu. Może pojawić się w dowolnym miejscu w treści **switch** instrukcji. Etykieta **case** lub **default** może wystąpić tylko wewnątrz **switch** instrukcji.

Typ **switch** *wyrażenia* i **case** *wyrażenia stałego* musi być liczbą całkowitą. Wartość każdego **case** *wyrażenia stałego* musi być unikatowa w treści instrukcji.

Etykiety **case** i **default** treści **switch** instrukcji są znaczące tylko w teście wstępnym, który określa, gdzie wykonywanie zostanie rozpoczęte w treści instrukcji. **switch** instrukcje mogą być zagnieżdżane. Wszystkie zmienne statyczne są inicjowane przed wykonaniem **switch** w instrukcjach.

> [!NOTE]
> Deklaracje mogą pojawić się w nagłówku złożonej instrukcji tworzącej **switch** treść, ale inicjalizacje zawarte w deklaracjach nie są wykonywane. **switch** Instrukcja przekazuje bezpośrednio formant do instrukcji wykonywalnej w treści, pomijając wiersze zawierające inicjalizacje.

W poniższych przykładach przedstawiono **switch** instrukcje:

```C
switch( c )
{
    case 'A':
        capital_a++;
    case 'a':
        letter_a++;
    default :
        total++;
}
```

Wszystkie trzy **switch** instrukcje treści w tym przykładzie są wykonywane `c` `'A'`, jeśli jest równe, ponieważ instrukcja nie **break** pojawia się przed poniższymi caseinstrukcjami. Sterowanie wykonywaniem jest przenoszone do pierwszej instrukcji`capital_a++;`() i kontynuuje w pozostałej części treści. Jeśli `c` wartość jest `'a'`równa `letter_a` i `total` jest zwiększana. Wartość `total` jest zwiększana tylko `c` wtedy, `'A'` gdy `'a'`nie jest równa lub.

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

W tym przykładzie instrukcja jest **break** zgodna z każdą instrukcją w **switch** treści. **break** Instrukcja wymusza wyjście z treści instrukcji po wykonaniu jednej instrukcji. Jeśli `i` wartość jest równa-1, `n` tylko jest zwiększana. **break** Poniższa instrukcja `n++;` powoduje, że kontrola wykonywania przeszedł z treści instrukcji, pomijając pozostałe instrukcje. Podobnie, jeśli `i` wartość jest równa 0, `z` wartość jest zwiększana tylko; Jeśli `i` wartość jest równa 1, `p` tylko jest zwiększana. Instrukcja Final **break** nie jest absolutnie konieczna, ponieważ kontrolka przechodzi poza treść na końcu złożonej instrukcji. Jest on uwzględniany w celu zapewnienia spójności.

Pojedyncza instrukcja może zawierać wiele **case** etykiet, jak pokazano w poniższym przykładzie:

```C
switch( c )
{
    case 'a' :
    case 'b' :
    case 'c' :
    case 'd' :
    case 'e' :
    case 'f' :  convert_hex(c);
}
```

W tym przykładzie, jeśli *wyrażenie stałe* jest równe dowolnej literze `'a'` między `'f'`i, `convert_hex` funkcja jest wywoływana.

### <a name="microsoft-specific"></a>specyficzne dla firmy Microsoft

Microsoft C nie ogranicza liczby case wartości w **switch** instrukcji. Liczba jest ograniczona tylko przez dostępną pamięć. ANSI C wymaga co najmniej 257 case etykiet w **switch** instrukcji.

W default przypadku oprogramowania Microsoft C są włączone rozszerzenia Microsoft. Aby wyłączyć te rozszerzenia, użyj opcji kompilatora [/za](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="see-also"></a>Zobacz także

[switchInstrukcja (C++)](../cpp/switch-statement-cpp.md)
