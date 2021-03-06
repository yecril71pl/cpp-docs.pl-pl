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
ms.openlocfilehash: 76e8abdaa2e2d0d8ba14209b45982b6a7f63f2e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227858"
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
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator* **=** *inicjator*

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>wybór</sub> wskaźnika *Direct-deklarator*

*Direct-deklarator*:/ \* A funkcja deklarator\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator***(***Typ parametru-list***)**   / \* New-Style deklarator      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator***(** nieważność*listy identyfikatorów*<sub>opt</sub> **)**  / \* — przestarzałe style deklarator    \*/

Prototyp ma ten sam formularz, który jest definicją funkcji, z tą różnicą, że jest zakończony średnikiem bezpośrednio po nawiasie zamykającym i w związku z tym nie ma treści. W obu przypadkach typ zwracany musi zgadzać się z typem zwracanym określonym w definicji funkcji.

Prototypy funkcji mają następujące ważne zastosowania:

- Określają typ zwracany dla funkcji, które zwracają typy inne niż **`int`** . Chociaż funkcje, które zwracają **`int`** wartości nie wymagają prototypów, zalecane są prototypy.

- Bez kompletnych prototypów są wykonywane standardowe konwersje, ale nie są podejmowane próby sprawdzenia typu lub liczby argumentów z liczbą parametrów.

- Prototypy są używane do inicjowania wskaźników do funkcji przed zdefiniowaniem tych funkcji.

- Lista parametrów służy do sprawdzania zgodności argumentów w wywołaniu funkcji z parametrami w definicji funkcji.

Przekonwertowany typ każdego parametru określa interpretację argumentów wywoływanych przez funkcję na stosie. Niezgodność typów między argumentem a parametrem może spowodować, że argumenty na stosie będą interpretowane nieprawidłowo. Na przykład na komputerze 16-bitowym, jeśli wskaźnik 16-bitowy jest przenoszona jako argument, zadeklarowany jako **`long`** parametr, pierwsze 32 bitów na stosie jest interpretowane jako **`long`** parametr. Ten błąd tworzy problemy nie tylko z **`long`** parametrem, ale z dowolnymi parametrami, które go obserwują. Możesz wykryć błędy tego rodzaju, deklarując kompletne prototypy funkcji dla wszystkich funkcji.

Prototyp tworzy atrybuty funkcji tak, aby wywołania funkcji, która poprzedza jej definicję (lub wystąpią w innych plikach źródłowych), można sprawdzić pod kątem typu argumentu i niezgodności typów zwracanych. Na przykład, jeśli określisz **`static`** specyfikator klasy magazynowania w prototypie, należy również określić **`static`** klasę magazynu w definicji funkcji.

Kompletne deklaracje parametrów ( `int a` ) mogą być mieszane z abstrakcyjną Deklaratory ( **`int`** ) w tej samej deklaracji. Na przykład następująca deklaracja ma charakter prawny:

```C
int add( int a, int );
```

Prototyp może zawierać zarówno typ, jak i identyfikator dla, każde wyrażenie, które jest przesyłane jako argument. Jednak takie identyfikatory mają zakres tylko do końca deklaracji. Prototyp może również odzwierciedlać fakt, że liczba argumentów jest zmienna lub że żadne argumenty nie są przekazane. Bez takiej listy niezgodne elementy mogą nie być ujawnione, więc kompilator nie może generować komunikatów diagnostycznych dotyczących ich. Zobacz [argumenty](../c-language/arguments.md) , aby uzyskać więcej informacji na temat sprawdzania typu.

Zakres prototypu w kompilatorze języka Microsoft C jest teraz zgodny ze standardem ANSI w przypadku kompilowania z użyciem opcji kompilatora **/za** . Oznacza to, że Jeśli zadeklarujesz **`struct`** **`union`** tag lub w obrębie prototypu, tag jest wprowadzany w tym zakresie, a nie w zakresie globalnym. Na przykład podczas kompilowania z **/za** dla zgodności ANSI, nigdy nie można wywołać tej funkcji bez uzyskiwania błędu niezgodności typów:

```C
void func1( struct S * );
```

Aby poprawić kod, Zdefiniuj lub Zadeklaruj **`struct`** lub **`union`** w zakresie globalnym przed prototypem funkcji:

```C
struct S;
void func1( struct S * );
```

W obszarze **/ze**tag nadal jest wprowadzany w zakresie globalnym.

## <a name="see-also"></a>Zobacz także

[Funkcje](../c-language/functions-c.md)
