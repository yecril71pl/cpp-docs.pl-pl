---
title: '#define, dyrektywa (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: e9e5b7a02ee55c05aa44278fbceb9c42f372c443
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506671"
---
# <a name="define-directive-cc"></a>#define — dyrektywa (C/C++)

**#Define** tworzy *makro*, czyli Skojarzenie identyfikatora lub identyfikatora sparametryzowanego z ciągiem tokenu. Po zdefiniowaniu makra kompilator może zastąpić ciąg tokenu dla każdego wystąpienia identyfikatora w pliku źródłowym.

## <a name="syntax"></a>Składnia

> token *identyfikatora* **#define** *—*<sub>wybór</sub> ciągu\
> **#define** *Identyfikator* **#define (** <sub>opt</sub>**o** *identyfikatorze*,... **,** *identifier*<sub>wybór</sub> **identyfikatora)** *—*<sub>wybór</sub> ciągu

## <a name="remarks"></a>Uwagi

Dyrektywa **#define** powoduje, że kompilator zastępuje *ciąg tokenów* dla każdego wystąpienia *identyfikatora* w pliku źródłowym. *Identyfikator* jest zamieniany tylko wtedy, gdy tworzy token. Oznacza to, że *Identyfikator* nie jest zastępowany, jeśli pojawia się w komentarzu, w ciągu lub jako część dłuższego identyfikatora. Aby uzyskać więcej informacji, zobacz [tokeny](../cpp/character-sets.md).

Argument *ciągu tokenu* składa się z serii tokenów, takich jak słowa kluczowe, stałe lub kompletne instrukcje. Co najmniej jeden znak odstępu musi oddzielać *ciąg tokenu* od *identyfikatora*. Ten biały znak nie jest uważany za część zastępowanego tekstu ani nie jest żadnym białym znakiem, który następuje po ostatnim tokenie tekstu.

A `#define` bez *ciągu tokenu* usuwa wystąpienia *identyfikatora* z pliku źródłowego. *Identyfikator* pozostaje zdefiniowany i może być testowany przy użyciu `#if defined` `#ifdef` dyrektyw i.

Druga forma składni definiuje makro podobne do funkcji z parametrami. Ten formularz przyjmuje opcjonalną listę parametrów, które muszą występować w nawiasach. Po zdefiniowaniu makra każde kolejne wystąpienie *identyfikatora*(<sub>opt</sub>o *identyfikatorze*,..., wybór *identyfikatora*<sub>opt</sub> ) jest zastępowane wersją argumentu *token-String* , który ma rzeczywiste argumenty zastępujące parametry formalne.

Nazwy parametrów formalnych są wyświetlane w *ciągu tokenu* , aby oznaczyć lokalizacje, w których są zastępowane wartości rzeczywiste. Nazwy poszczególnych parametrów mogą występować wiele razy w *ciągu tokenu*, a nazwy mogą pojawiać się w dowolnej kolejności. Liczba argumentów w wywołaniu musi być zgodna z liczbą parametrów w definicji makra. Liberalizacja użycia nawiasów gwarantuje, że złożone rzeczywiste argumenty są poprawnie interpretowane.

Parametry formalne na liście są oddzielone przecinkami. Każda nazwa na liście musi być unikatowa, a lista musi być ujęta w nawiasy. Spacje nie mogą oddzielać *identyfikatora* i nawiasu otwierającego. Użyj łączenia linii — Umieść ukośnik odwrotny ( `\` ) bezpośrednio przed znakiem nowego wiersza — dla długich dyrektyw w wielu wierszach źródła. Zakres nazwy parametru formalnego rozciąga się do nowego wiersza, który zawiera *ciąg tokenu*.

Gdy makro zostało zdefiniowane w drugim formularzu składni, kolejne wystąpienia tekstowe, po których następuje lista argumentów, wskazują na wywołanie makra. Rzeczywiste argumenty występujące po wystąpieniu *identyfikatora* w pliku źródłowym są dopasowywane do odpowiednich parametrów formalnych w definicji makra. Każdy parametr formalny w *ciągu tokenu* , który nie jest poprzedzony tworzenia ciągu ( `#` ), konwersji na znaki ( `#@` ), lub wklejanie tokenu ( `##` ), lub nie następuje przez `##` operatora, jest zastępowany odpowiadającym mu argumentem rzeczywistym. Wszystkie makra w rzeczywistym argumencie są rozwinięte przed zastąpieniem parametru formalnego przez dyrektywę. (Operatory są opisane w [operatorach preprocesora](../preprocessor/preprocessor-operators.md)).

Poniższe przykłady makr z argumentami ilustrują drugą formę składni **#define** :

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

Argumenty z efektami ubocznymi czasami powodują, że makra generują nieoczekiwane wyniki. Dany parametr formalny może pojawić się więcej niż jeden raz w *ciągu tokenu*. Jeśli ten parametr formalny jest zastępowany przez wyrażenie z efektami ubocznymi, wyrażenie z efektami ubocznymi może być oceniane więcej niż jeden raz. (Zobacz przykłady w obszarze [operator wklejania tokenu (# #)](../preprocessor/token-pasting-operator-hash-hash.md).)

`#undef`Dyrektywa powoduje, że definicja preprocesora identyfikatora zostanie zapomniana. Aby uzyskać więcej informacji [, zobacz dyrektywę #undef](../preprocessor/hash-undef-directive-c-cpp.md) .

Jeśli nazwa definiowanego makra występuje w *ciągu tokenu* (nawet w wyniku innego rozwinięcia makra), nie jest rozwinięta.

Druga **#define** dla makra o tej samej nazwie generuje ostrzeżenie, chyba że druga sekwencja tokenów jest taka sama jak pierwsza.

**Specyficzne dla firmy Microsoft**

Język Microsoft C/C++ umożliwia ponowne zdefiniowanie makra, jeśli nowa definicja jest syntaktycznie identyczna z oryginalną definicją. Innymi słowy, dwie definicje mogą mieć różne nazwy parametrów. To zachowanie różni się od ANSI C, które wymaga, aby dwie definicje były identyczne.

Na przykład następujące dwa makra są identyczne, z wyjątkiem nazw parametrów. ANSI C nie zezwala na taką ponowną definicję, ale firma Microsoft C/C++ kompiluje ją bez błędu.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

Z drugiej strony następujące dwa makra nie są identyczne i wygenerują ostrzeżenie w Microsoft C/C++.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Ten przykład ilustruje **#define** dyrektywie:

```C
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```

Pierwsza instrukcja definiuje identyfikator `WIDTH` jako stałą liczbę całkowitą 80 i definiuje jako całkowitą `LENGTH` `WIDTH` stałą 10. Każde wystąpienie `LENGTH` jest zastępowane przez ( `WIDTH + 10` ). Z kolei każde wystąpienie `WIDTH + 10` jest zastępowane wyrażeniem ( `80 + 10` ). Nawiasy `WIDTH + 10` są ważne, ponieważ kontrolują interpretację instrukcji, takich jak następujące:

```C
var = LENGTH * 20;
```

Po etapie przetwarzania wstępnego instrukcja zostanie wystawiona:

```C
var = ( 80 + 10 ) * 20;
```

który ma wartość 1800. Bez nawiasów, wynik:

```C
var = 80 + 10 * 20;
```

który ma wartość 280.

**Specyficzne dla firmy Microsoft**

Definiowanie makr i stałych z opcją [/d](../build/reference/d-preprocessor-definitions.md) kompilatora ma ten sam efekt, co użycie dyrektywy **#define** na początku pliku. Do 30 makr można zdefiniować przy użyciu/D opcji.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)
