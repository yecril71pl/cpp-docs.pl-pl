---
title: Prototypy funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function prototypes
- function return types, function prototypes
- data types [C], function return types
- functions [C], return types
- prototypes [C++], function
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
ms.openlocfilehash: 9c42ce5b23e6f755dafd57bdb5a5f79cf1adb4ec
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857089"
---
# <a name="function-prototypes"></a>Prototypy funkcji

Deklaracja funkcji poprzedza definicję funkcji i określa nazwę, typ zwracany, klasę magazynu i inne atrybuty funkcji. Aby być prototypem, deklaracja funkcji musi również określać typy i identyfikatory dla argumentów funkcji.

## <a name="syntax"></a>Składnia

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja-specyfikators* *-SEQ*<sub>opt</sub> *init-deklarator-list*<sub>opt</sub> **;**

/\**atrybut-seq*<sub>opt</sub> to specyficzny dla firmy Microsoft\*/

*specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja* *specyfikatora klasy magazynu* —<sub>wybór</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *specyfikatora typu* *— wybór specyfikatorów*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *kwalifikatora typu* *— wybór specyfikatorów*<sub>opt</sub>

*init-deklarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator-list*  **,**  *init-deklarator*

*init-deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *inicjator* deklarator

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>wybór</sub> wskaźnika *Direct-deklarator*

*Direct-deklarator*:/\* A funkcja deklarator\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator***(***Typ parametru-list***)**   / \* New-Style deklarator      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator***(** nieważność*listy identyfikatorów*<sub>opt</sub> **)**  / \* — przestarzałe style deklarator    \*/

Prototyp ma ten sam formularz, który jest definicją funkcji, z tą różnicą, że jest zakończony średnikiem bezpośrednio po nawiasie zamykającym i w związku z tym nie ma treści. W obu przypadkach typ zwracany musi zgadzać się z typem zwracanym określonym w definicji funkcji.

Prototypy funkcji mają następujące ważne zastosowania:

- Określają typ zwracany dla funkcji, które zwracają typy inne niż **int**. Chociaż funkcje, które zwracają wartości **int** , nie wymagają prototypów, zalecane są prototypy.

- Bez kompletnych prototypów są wykonywane standardowe konwersje, ale nie są podejmowane próby sprawdzenia typu lub liczby argumentów z liczbą parametrów.

- Prototypy są używane do inicjowania wskaźników do funkcji przed zdefiniowaniem tych funkcji.

- Lista parametrów służy do sprawdzania zgodności argumentów w wywołaniu funkcji z parametrami w definicji funkcji.

Przekonwertowany typ każdego parametru określa interpretację argumentów wywoływanych przez funkcję na stosie. Niezgodność typów między argumentem a parametrem może spowodować, że argumenty na stosie będą interpretowane nieprawidłowo. Na przykład na komputerze 16-bitowym, jeśli wskaźnik 16-bitowy jest przenoszona jako argument, zadeklarowany jako parametr **Long** , pierwsze 32 bitów na stosie jest interpretowane jako **Long** Parameter. Ten błąd tworzy problemy nie tylko z **długim** parametrem, ale z dowolnymi parametrami, które je obserwują. Możesz wykryć błędy tego rodzaju, deklarując kompletne prototypy funkcji dla wszystkich funkcji.

Prototyp tworzy atrybuty funkcji tak, aby wywołania funkcji, która poprzedza jej definicję (lub wystąpią w innych plikach źródłowych), można sprawdzić pod kątem typu argumentu i niezgodności typów zwracanych. Na przykład, jeśli określisz **statyczny** specyfikator klasy magazynu w prototypie, należy również określić klasę magazynu **statycznego** w definicji funkcji.

Kompletne deklaracje parametrów`int a`() mogą być mieszane z abstrakcyjną`int`Deklaratory () w tej samej deklaracji. Na przykład następująca deklaracja ma charakter prawny:

```C
int add( int a, int );
```

Prototyp może zawierać zarówno typ, jak i identyfikator dla, każde wyrażenie, które jest przesyłane jako argument. Jednak takie identyfikatory mają zakres tylko do końca deklaracji. Prototyp może również odzwierciedlać fakt, że liczba argumentów jest zmienna lub że żadne argumenty nie są przekazane. Bez takiej listy niezgodne elementy mogą nie być ujawnione, więc kompilator nie może generować komunikatów diagnostycznych dotyczących ich. Zobacz [argumenty](../c-language/arguments.md) , aby uzyskać więcej informacji na temat sprawdzania typu.

Zakres prototypu w kompilatorze języka Microsoft C jest teraz zgodny ze standardem ANSI w przypadku kompilowania z użyciem opcji kompilatora **/za** . Oznacza to, że w przypadku deklarowania w prototypie tagu **struktury** lub **Unii** , znacznik jest wprowadzany w tym zakresie, a nie w zakresie globalnym. Na przykład podczas kompilowania z **/za** dla zgodności ANSI, nigdy nie można wywołać tej funkcji bez uzyskiwania błędu niezgodności typów:

```C
void func1( struct S * );
```

Aby poprawić kod, Zdefiniuj lub Zadeklaruj **strukturę** lub **Unię** w zakresie globalnym przed prototypem funkcji:

```C
struct S;
void func1( struct S * );
```

W obszarze **/ze**tag nadal jest wprowadzany w zakresie globalnym.

## <a name="see-also"></a>Zobacz też

[Funkcje](../c-language/functions-c.md)
