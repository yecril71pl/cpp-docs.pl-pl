---
title: :::no-loc(switch):::Instrukcja (C)
ms.date: 04/25/2020
f1_keywords:
- ':::no-loc(switch):::'
helpviewer_keywords:
- ':::no-loc(switch)::: keyword [C]'
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- ':::no-loc(switch):::'
- ':::no-loc(case):::'
- ':::no-loc(default):::'
- ':::no-loc(break):::'
ms.openlocfilehash: bdd6885f67728a3c81e395f05c33191156896ad9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220785"
---
# <a name="no-locswitch-statement-c"></a>`:::no-loc(switch):::`Instrukcja (C)

**`:::no-loc(switch):::`** Instrukcje i **`:::no-loc(case):::`** ułatwiają kontrolę złożonych operacji warunkowych i rozgałęzień. **`:::no-loc(switch):::`** Instrukcja przekazuje formant do instrukcji w jej treści.

## <a name="syntax"></a>Składnia

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(switch)::: (`**&nbsp;*`expression`* &nbsp;**`)`**&nbsp;*`statement`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(case):::`**&nbsp;*`constant-expression`*&nbsp;**`:`**&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(default):::`**&nbsp;**`:`**&nbsp;*`statement`*

## <a name="remarks"></a>Uwagi

**`:::no-loc(switch):::`** Instrukcja powoduje, że kontrolka jest przekazywana do jednego *`labeled-statement`* w jego treści instrukcji, w zależności od wartości *`expression`* .

Wartości *`expression`* i każdego z nich *`constant-expression`* muszą mieć typ całkowity. A *`constant-expression`* musi mieć niejednoznaczną stałą wartość całkowitą w czasie kompilacji.

Kontrolka przechodzi do **`:::no-loc(case):::`** instrukcji, której *`constant-expression`* wartość jest zgodna z wartością *`expression`* . **`:::no-loc(switch):::`** Instrukcja może zawierać dowolną liczbę **`:::no-loc(case):::`** wystąpień. Jednak żadne dwie *`constant-expression`* wartości w tej samej **`:::no-loc(switch):::`** instrukcji nie mogą mieć tej samej wartości. Wykonywanie **`:::no-loc(switch):::`** treści instrukcji rozpoczyna się od pierwszej instrukcji w lub po dopasowaniu *`labeled-statement`* . Wykonywanie przechodzi do końca treści lub do momentu, aż **`:::no-loc(break):::`** instrukcja przeniesie kontrolę z treści.

Użycie **`:::no-loc(switch):::`** instrukcji zwykle wygląda następująco:

```C
:::no-loc(switch)::: ( expression )
{
    // declarations
    // . . .
    :::no-loc(case)::: constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        :::no-loc(break):::;
    :::no-loc(default)::::
        // statements executed if expression does not equal
        // any :::no-loc(case)::: constant_expression
}
```

Możesz użyć instrukcji, **`:::no-loc(break):::`** Aby zakończyć przetwarzanie konkretnej instrukcji oznaczonej etykietą w **`:::no-loc(switch):::`** instrukcji. Oddziały IT do końca **`:::no-loc(switch):::`** instrukcji. Bez **`:::no-loc(break):::`** , program przechodzi do następnej instrukcji oznaczonej etykietą, wykonując instrukcje do momentu **`:::no-loc(break):::`** osiągnięcia lub zakończenia instrukcji. Kontynuacja może być pożądana w niektórych sytuacjach.

**`:::no-loc(default):::`** Instrukcja jest wykonywana, jeśli żadna **`:::no-loc(case):::`** *`constant-expression`* wartość nie jest równa wartości *`expression`* . Jeśli nie ma żadnej **`:::no-loc(default):::`** instrukcji i nie **`:::no-loc(case):::`** znaleziono dopasowania, żadna z instrukcji w treści nie zostanie **`:::no-loc(switch):::`** wykonana. Może istnieć co najwyżej jedna **`:::no-loc(default):::`** instrukcja. **`:::no-loc(default):::`** Instrukcja nie musi znajdować się na końcu. Może pojawić się w dowolnym miejscu w treści **`:::no-loc(switch):::`** instrukcji. **`:::no-loc(case):::`** Etykieta lub **`:::no-loc(default):::`** może wystąpić tylko wewnątrz **`:::no-loc(switch):::`** instrukcji.

Typ **`:::no-loc(switch):::`** *`expression`* i **`:::no-loc(case):::`** *`constant-expression`* musi być liczbą całkowitą. Wartość każdego z nich **`:::no-loc(case):::`** *`constant-expression`* musi być unikatowa w treści instrukcji.

**`:::no-loc(case):::`** Etykiety i **`:::no-loc(default):::`** **`:::no-loc(switch):::`** treści instrukcji są znaczące tylko w teście wstępnym, który określa, gdzie wykonywanie zostanie rozpoczęte w treści instrukcji. **`:::no-loc(switch):::`** instrukcje mogą być zagnieżdżane. Wszystkie zmienne statyczne są inicjowane przed wykonaniem w **`:::no-loc(switch):::`** instrukcjach.

> [!NOTE]
> Deklaracje mogą pojawić się w nagłówku złożonej instrukcji tworzącej **`:::no-loc(switch):::`** treść, ale inicjalizacje zawarte w deklaracjach nie są wykonywane. **`:::no-loc(switch):::`** Instrukcja przekazuje bezpośrednio formant do instrukcji wykonywalnej w treści, pomijając wiersze zawierające inicjalizacje.

W poniższych przykładach przedstawiono **`:::no-loc(switch):::`** instrukcje:

```C
:::no-loc(switch):::( c )
{
    :::no-loc(case)::: 'A':
        capital_a++;
    :::no-loc(case)::: 'a':
        letter_a++;
    :::no-loc(default)::: :
        total++;
}
```

Wszystkie trzy instrukcje **`:::no-loc(switch):::`** treści w tym przykładzie są wykonywane `c` , jeśli jest równe `'A'` , ponieważ **`:::no-loc(break):::`** instrukcja nie pojawia się przed poniższymi instrukcjami **`:::no-loc(case):::`** . Sterowanie wykonywaniem jest przenoszone do pierwszej instrukcji ( `capital_a++;` ) i kontynuuje w pozostałej części treści. Jeśli `c` wartość jest równa `'a'` `letter_a` i jest `total` zwiększana. `total`Wartość jest zwiększana tylko wtedy `c` , gdy nie jest równa `'A'` lub `'a'` .

```C
:::no-loc(switch):::( i )
{
    :::no-loc(case)::: -1:
        n++;
        :::no-loc(break):::;
    :::no-loc(case)::: 0 :
        z++;
        :::no-loc(break):::;
    :::no-loc(case)::: 1 :
        p++;
        :::no-loc(break):::;
}
```

W tym przykładzie instrukcja jest **`:::no-loc(break):::`** zgodna z każdą instrukcją w **`:::no-loc(switch):::`** treści. **`:::no-loc(break):::`** Instrukcja wymusza wyjście z treści instrukcji po wykonaniu jednej instrukcji. Jeśli `i` wartość jest równa-1, tylko `n` jest zwiększana. **`:::no-loc(break):::`** Poniższa instrukcja `n++;` powoduje, że kontrola wykonywania przeszedł z treści instrukcji, pomijając pozostałe instrukcje. Podobnie, jeśli `i` wartość jest równa 0, tylko `z` jest zwiększana `i` . Jeśli wartość jest równa 1, tylko `p` jest zwiększana. Instrukcja Final **`:::no-loc(break):::`** nie jest absolutnie konieczna, ponieważ kontrolka przechodzi poza treść na końcu złożonej instrukcji. Jest on uwzględniany w celu zapewnienia spójności.

Pojedyncza instrukcja może zawierać wiele **`:::no-loc(case):::`** etykiet, jak pokazano w poniższym przykładzie:

```C
:::no-loc(switch):::( c )
{
    :::no-loc(case)::: 'a' :
    :::no-loc(case)::: 'b' :
    :::no-loc(case)::: 'c' :
    :::no-loc(case)::: 'd' :
    :::no-loc(case)::: 'e' :
    :::no-loc(case)::: 'f' :  convert_hex(c);
}
```

W tym przykładzie, jeśli *wyrażenie stałe* jest równe dowolnej literze między `'a'` i `'f'` , `convert_hex` Funkcja jest wywoływana.

### <a name="microsoft-specific"></a>specyficzne dla firmy Microsoft

Microsoft C nie ogranicza liczby **`:::no-loc(case):::`** wartości w **`:::no-loc(switch):::`** instrukcji. Liczba jest ograniczona tylko przez dostępną pamięć. ANSI C wymaga co najmniej 257 **`:::no-loc(case):::`** etykiet w **`:::no-loc(switch):::`** instrukcji.

W :::no-loc(default)::: przypadku oprogramowania Microsoft C są włączone rozszerzenia Microsoft. Aby wyłączyć te rozszerzenia, użyj opcji kompilatora [/za](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="see-also"></a>Zobacz także

[:::no-loc(switch):::Instrukcja (C++)](../cpp/:::no-loc(switch):::-statement-cpp.md)
