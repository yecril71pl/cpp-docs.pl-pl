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
ms.openlocfilehash: eb18b6244318b595e67cc45f99dfcde314866f55
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825681"
---
# <a name="switch-statement-c"></a>`switch`Instrukcja (C)

Instrukcje __`switch`__ i __`case`__ ułatwiają kontrolę złożonych operacji warunkowych i rozgałęzień. __`switch`__ Instrukcja przekazuje formant do instrukcji w jej treści.

## <a name="syntax"></a>Składnia

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`switch (`__&nbsp;*`expression`* &nbsp;__`)`__&nbsp;*`statement`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>Uwagi

Instrukcja __`switch`__ powoduje, że kontrolka jest przekazywana do jednego *`labeled-statement`* w jego treści instrukcji, w zależności od *`expression`* wartości.

Wartości i każdego *`expression`* z nich *`constant-expression`* muszą mieć typ całkowity. A *`constant-expression`* musi mieć niejednoznaczną stałą wartość całkowitą w czasie kompilacji.

Kontrolka przechodzi do **`case`** instrukcji, *`constant-expression`* której wartość jest zgodna z *`expression`* wartością. __`switch`__ Instrukcja może zawierać dowolną liczbę __`case`__ wystąpień. Jednak żadne dwie *`constant-expression`* wartości w tej samej __`switch`__ instrukcji nie mogą mieć tej samej wartości. Wykonywanie treści __`switch`__ instrukcji rozpoczyna się od pierwszej instrukcji w lub po dopasowaniu *`labeled-statement`*. Wykonywanie przechodzi do końca treści lub do momentu, aż __`break`__ instrukcja przeniesie kontrolę z treści.

Użycie __`switch`__ instrukcji zwykle wygląda następująco:

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

Możesz użyć instrukcji, __`break`__ aby zakończyć przetwarzanie konkretnej instrukcji oznaczonej etykietą w __`switch`__ instrukcji. Oddziały IT do końca __`switch`__ instrukcji. Bez __`break`__, program przechodzi do następnej instrukcji oznaczonej etykietą, wykonując instrukcje do momentu osiągnięcia __`break`__ lub zakończenia instrukcji. Kontynuacja może być pożądana w niektórych sytuacjach.

Instrukcja __`default`__ jest wykonywana, jeśli żadna __`case`__ *`constant-expression`* wartość nie jest równa wartości *`expression`*. Jeśli nie ma żadnej __`default`__ instrukcji i nie __`case`__ znaleziono dopasowania, żadna z instrukcji w __`switch`__ treści nie zostanie wykonana. Może istnieć co najwyżej jedna __`default`__ instrukcja. __`default`__ Instrukcja nie musi znajdować się na końcu. Może pojawić się w dowolnym miejscu w treści __`switch`__ instrukcji. Etykieta __`case`__ lub __`default`__ może wystąpić tylko wewnątrz __`switch`__ instrukcji.

Typ __`switch`__ *`expression`* __`case`__ i *`constant-expression`* musi być liczbą całkowitą. Wartość każdego z nich __`case`__ *`constant-expression`* musi być unikatowa w treści instrukcji.

Etykiety __`case`__ i __`default`__ treści __`switch`__ instrukcji są znaczące tylko w teście wstępnym, który określa, gdzie wykonywanie zostanie rozpoczęte w treści instrukcji. __`switch`__ instrukcje mogą być zagnieżdżane. Wszystkie zmienne statyczne są inicjowane przed wykonaniem __`switch`__ w instrukcjach.

> [!NOTE]
> Deklaracje mogą pojawić się w nagłówku złożonej instrukcji tworzącej __`switch`__ treść, ale inicjalizacje zawarte w deklaracjach nie są wykonywane. __`switch`__ Instrukcja przekazuje bezpośrednio formant do instrukcji wykonywalnej w treści, pomijając wiersze zawierające inicjalizacje.

W poniższych przykładach przedstawiono __`switch`__ instrukcje:

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

Wszystkie trzy __`switch`__ instrukcje treści w tym przykładzie są wykonywane `c` `'A'`, jeśli jest równe, ponieważ instrukcja nie __`break`__ pojawia się przed poniższymi __`case`__ instrukcjami. Sterowanie wykonywaniem jest przenoszone do pierwszej instrukcji`capital_a++;`() i kontynuuje w pozostałej części treści. Jeśli `c` wartość jest `'a'`równa `letter_a` i `total` jest zwiększana. Wartość `total` jest zwiększana tylko `c` wtedy, `'A'` gdy `'a'`nie jest równa lub.

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

W tym przykładzie instrukcja jest __`break`__ zgodna z każdą instrukcją w __`switch`__ treści. __`break`__ Instrukcja wymusza wyjście z treści instrukcji po wykonaniu jednej instrukcji. Jeśli `i` wartość jest równa-1, `n` tylko jest zwiększana. __`break`__ Poniższa instrukcja `n++;` powoduje, że kontrola wykonywania przeszedł z treści instrukcji, pomijając pozostałe instrukcje. Podobnie, jeśli `i` wartość jest równa 0, `z` wartość jest zwiększana tylko; Jeśli `i` wartość jest równa 1, `p` tylko jest zwiększana. Instrukcja Final __`break`__ nie jest absolutnie konieczna, ponieważ kontrolka przechodzi poza treść na końcu złożonej instrukcji. Jest on uwzględniany w celu zapewnienia spójności.

Pojedyncza instrukcja może zawierać wiele __`case`__ etykiet, jak pokazano w poniższym przykładzie:

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

Microsoft C nie ogranicza liczby __`case`__ wartości w __`switch`__ instrukcji. Liczba jest ograniczona tylko przez dostępną pamięć. ANSI C wymaga co najmniej 257 __`case`__ etykiet w __`switch`__ instrukcji.

W default przypadku oprogramowania Microsoft C są włączone rozszerzenia Microsoft. Aby wyłączyć te rozszerzenia, użyj opcji kompilatora [/za](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="see-also"></a>Zobacz też

[switchInstrukcja (C++)](../cpp/switch-statement-cpp.md)
