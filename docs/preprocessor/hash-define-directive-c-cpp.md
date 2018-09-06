---
title: '##define — dyrektywa (C/C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#define'
dev_langs:
- C++
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e24c7e020f0008a78d4595577c656003bad359c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765684"
---
# <a name="define-directive-cc"></a>#define — dyrektywa (C/C++)

**#Define** tworzy *— makro*, który jest skojarzenie identyfikatora lub identyfikatora sparametryzowanej ciągiem tokenu. Po zdefiniowaniu makra kompilator może zastąpić ciąg tokenu dla każdego wystąpienia identyfikatora w pliku źródłowym.

## <a name="syntax"></a>Składnia

`#define` *Identyfikator* *ciąg tokenu*<sub>zoptymalizowany pod kątem</sub>

`#define` *Identyfikator* `(` *identyfikator*<sub>zoptymalizowany pod kątem</sub> `,` *...*  `,` *identyfikator*<sub>zoptymalizowany pod kątem</sub> `)` *ciąg tokenu*<sub>zoptymalizowany pod kątem</sub>

## <a name="remarks"></a>Uwagi

**#Define** dyrektywy powoduje, że kompilator podstawia *ciąg tokenu* dla każdego wystąpienia *identyfikator* w pliku źródłowym. *Identyfikator* jest zastępowany tylko wtedy, gdy stanowi token. Oznacza to, że *identyfikator* nie jest zastępowany, jeśli występuje on w komentarzu, w ciągu lub jako część dłuższego identyfikatora. Aby uzyskać więcej informacji, zobacz [tokenów](../cpp/tokens-cpp.md).

*Ciąg tokenu* argument składa się z serii tokenów, takich jak słowa kluczowe, stałe lub pełne instrukcje. Muszą być rozdzielone przez co najmniej jeden znak odstępu *ciąg tokenu* z *identyfikator*. Ten biały znak nie jest uważany za część podstawionego tekstu, podobnie jak dowolny biały obszar, który następuje po ostatnim tokenem tekstu.

A `#define` bez *ciąg tokenu* usuwa wystąpień *identyfikator* z pliku źródłowego. *Identyfikator* pozostaje zdefiniowany i może być przetestowany przy użyciu `#if defined` i `#ifdef` dyrektywy.

Druga forma składni definiuje funkcyjne makro za pomocą parametrów. Ten formularz przyjmuje opcjonalną listę parametrów, które muszą być ujęte w nawiasy. Po makro jest zdefiniowany, każde kolejne wystąpienie *identyfikator*( *identyfikator*<sub>zoptymalizowany pod kątem</sub>,..., *identyfikator* <sub>zoptymalizowany pod kątem</sub> ) jest zastępowany przy użyciu wersji *ciąg tokenu* argumentu, który zawiera rzeczywiste argumenty podstawiane dla parametrów formalnych.

Nazwy parametrów formalnych pojawiają się w *ciąg tokenu* do oznaczania miejsc, w których są zastępowane wartości rzeczywiste. Nazwa każdego parametru może pojawić się wiele razy w *ciąg tokenu*, a nazwy mogą być wyświetlane w dowolnej kolejności. Liczba argumentów w wywołaniu musi odpowiadać liczbie parametrów w definicji makra. Liberalne stosowanie nawiasów gwarantuje poprawną interpretację złożonych bieżących argumentów.

Parametry formalne na liście są oddzielone przecinkami. Każda nazwa na liście musi być unikatowa, a listy muszą być ujęte w nawiasy. Żadne spacje nie mogą rozdzielić *identyfikator* i nawias otwierający. Użyj łączenia wierszy — umieść ukośnik odwrotny (`\`) bezpośrednio przed znakiem nowego wiersza — dla długich dyrektyw w wielu wierszach źródłowych. Zakres formalnego parametru rozciąga się do nowej linii, która kończy się *ciąg tokenu*.

Po zdefiniowaniu makra w drugim formularzu składni, kolejne wystąpienia tekstowe następuje lista argumentów oznaczają wywołanie makro. Rzeczywiste argumenty, które następują po wystąpieniu *identyfikator* w pliku źródłowym są dopasowywane do odpowiednich parametrów formalnych w definicji makra. Każdy z parametrów formalnych w *ciąg tokenu* nie jest poprzedzony przez ciąg (`#`), charizing (`#@`), lub wklejanie tokenów (`##`) operator, lub nie następuje `##` jest operator zastępuje odpowiednie argumenty rzeczywiste. Wszystkie makra w rzeczywistym argumencie są rozwinięte, zanim dyrektywa zastąpi parametrów formalny. (Operatorzy są opisani w [operatorach Preprocesowych](../preprocessor/preprocessor-operators.md).)

Poniższe przykłady makr z argumentami ilustrują drugą formę z **#define** składni:

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

Argumenty ze skutami ubocznych czasami powodują, że makra dają nieoczekiwane wyniki. Określony parametr formalny może pojawić się więcej niż jeden raz w *ciąg tokenu*. Jeśli ten parametr formalny zostanie zastąpiony przez wyrażenie z efektami ubocznymi, wyrażenie razem z efektami ubocznymi może ocenione więcej niż jeden raz. (Zobacz przykłady w [Operator wklejania tokenu (##)](../preprocessor/token-pasting-operator-hash-hash.md).)

`#undef` Dyrektywy powoduje, że identyfikator definicji preprocesora usunięcie. Zobacz [dyrektywa #undef](../preprocessor/hash-undef-directive-c-cpp.md) Aby uzyskać więcej informacji.

Jeśli nazwa definiowanego makra występuje w *ciąg tokenu* (nawet w wyniku innego makra rozszerzenia), to nie jest rozwinięta.

Sekundy **#define** dla makra o takiej samej nazwie generuje ostrzeżenie, o ile nie jest identyczny z pierwszym drugiej sekwencji tokenu.

**Microsoft Specific**

Microsoft C/C++ pozwala na zdefiniowanie makra, jeśli nowa definicja jest syntaktycznie identyczna odpowiadają oryginalnej definicji. Innymi słowy dwie definicje mogą mieć nazwy różnych parametrów. To zachowanie różni się od ANSI C, który wymaga leksykalnej obu definicji.

Na przykład następujące dwa makra są identyczne, z wyjątkiem nazw parametrów. ANSI C nie zezwala na taką ponowną definicję, ale Microsoft C/C++ kompiluje to bez błędu.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

Z drugiej strony dwa następujące makra nie są identyczne i generują ostrzeżenie w Microsoft C/C++.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**END specyficzny dla Microsoft**

Ten przykład ilustruje **#define** dyrektywy:

```C
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```

Pierwsza instrukcja Określa identyfikator `WIDTH` jako liczba całkowita stałej 80 i definiuje `LENGTH` pod względem `WIDTH` i liczbę całkowitą 10. Każde wystąpienie `LENGTH` zastępuje się wyrazami (`WIDTH + 10`). Z kolei, każde wystąpienie `WIDTH + 10` jest zastąpione wyrażeniem (`80 + 10`). Nawiasy wokół `WIDTH + 10` są ważne, ponieważ kontrolują interpretację instrukcji takich jak następujące:

```C
var = LENGTH * 20;
```

Po etapie przetwarzania wstępnego oświadczenie staje się:

```C
var = ( 80 + 10 ) * 20;
```

który ocenia do 1800. Bez nawiasów wynik jest:

```C
var = 80 + 10 * 20;
```

który ocenia do 280.

**Microsoft Specific**

Definiowanie makr i stałych z [/D](../build/reference/d-preprocessor-definitions.md) — opcja kompilatora ma ten sam efekt jak użycie **#define** dyrektywy preprocesora na początku pliku. Do 30 makr można zdefiniować przy użyciu opcji/d.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)