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
ms.openlocfilehash: 2c75db3e1550927af57054a2cc1561d9df1567a4
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148807"
---
# <a name="function-prototypes"></a>Prototypy funkcji

Deklaracja funkcji poprzedza definicji funkcji i określa nazwę, typ zwracany, klasę magazynu i innych atrybutów funkcji. Jako prototyp, deklaracji funkcji należy również określić typy i identyfikatory dla argumentów funkcji.

## <a name="syntax"></a>Składnia

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *attribute-seq*<sub>opt</sub> *init-declarator-list*<sub>opt</sub> **;**

/\* *Atrybut seq*<sub>zoptymalizowany pod kątem</sub> jest Specific dla Microsoft \*/

*Specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub>

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list*  **,**  *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator* **=** *inicjatora*

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *deklaratora bezpośrednie*

*deklarator bezpośrednio*: /\* deklaratora funkcji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio***(***listy parametrów typu***)**   / \* deklaratora nowy styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio***(***listy identyfikatorów*<sub>zoptymalizowany pod kątem</sub> **)**  / \* Obsolete stylu deklarator \*/

Prototyp ma tę samą postać co definicji funkcji, z tą różnicą, że jest zakończona średnikiem, natychmiast po zamykającym i dlatego ma bez treści. W obu przypadkach typ zwracany należy uzgodnić z typem zwracanym, określonym w definicji funkcji.

Prototypy funkcji ma następujące zastosowania ważnych:

- Określają typ zwracany dla funkcji, które zwracają typów innych niż **int**. Chociaż funkcje zwracają **int** wartości nie wymagają prototypy, prototypy są zalecane.

- Bez pełną prototypy konwersje standardowe są wykonywane, ale nie jest podejmowane próby sprawdź typ lub liczbą argumentów z liczbą parametrów.

- Prototypy są stosowane do inicjalizacji wskaźników do funkcji, zanim funkcje te są zdefiniowane.

- Lista parametrów jest używany do sprawdzania zgodności argumentów w wywołaniu funkcji przy użyciu parametrów w definicji funkcji.

Przekonwertowana typ każdego parametru określa interpretacji argumenty, które wywołanie funkcji miejsca na stosie. Niezgodność typu argumentu i parametru może spowodować argumenty na stosie, aby być niemożliwe. Na przykład na komputerze 16-bitowych, jeśli wskaźnik 16-bitowy jest przekazywany jako argument, następnie zadeklarowane jako **długie** parametru pierwsze 32 bity na stosie są interpretowane jako **długie** parametru. Ten błąd stwarza problemy, które nie tylko w przypadku **długie** parametru, ale wszystkie parametry, które występują po nim. DEKLARUJĄC prototypy funkcji ukończone dla wszystkich funkcji, można wykrywać błędy tego typu.

Prototyp ustanawia atrybutów funkcji tak, aby wywołania do funkcji, które poprzedzają jego definicji (lub wystąpić w innych plikach źródłowych) można sprawdzić typ argumentu i niezgodności zwracanego typu. Na przykład, jeśli określisz **statyczne** — Specyfikator klasy magazynowania w prototyp, należy także określić **statyczne** klasy magazynu w definicji funkcji.

Wykonaj deklaracji parametrów (`int a`) mogą być mieszane z deklaratory abstrakcyjne (`int`) w jednej deklaracji. Na przykład następująca deklaracja jest dozwolony:

```C
int add( int a, int );
```

Prototyp może zawierać typ i identyfikator, każde wyrażenie, który jest przekazywany jako argument. Jednak takie identyfikatory mają zakres tylko do końca deklaracji. Prototyp można również odzwierciedlają fakt, że liczba argumentów jest zmienna lub nie nich argumentów. Bez tych listy niezgodności może nie są ujawniane, dzięki czemu kompilator nie może wygenerować komunikaty diagnostyczne dotyczące ich. Zobacz [argumenty](../c-language/arguments.md) więcej informacji na temat sprawdzania typu.

Zakres prototypu w kompilatorze Microsoft C jest teraz ze standardem ANSI, podczas kompilowania za pomocą **/Za** — opcja kompilatora. Oznacza to, że jeśli zadeklarujesz **struktury** lub **Unii** tagu w ciągu prototypów, tagu jest wprowadzana w tym zakresie, a nie w zakresie globalnym. Na przykład podczas kompilowania za pomocą **/Za** zgodności z ANSI, może nigdy nie Wywołaj tę funkcję, bez błąd niezgodności typów:

```C
void func1( struct S * );
```

Aby poprawić kod, należy zdefiniować lub deklarowania **struktury** lub **Unii** w zakresie globalnym przed prototypu funkcji:

```C
struct S;
void func1( struct S * );
```

W obszarze **/Ze**, tagu jest nadal wprowadzony w zakresie globalnym.

## <a name="see-also"></a>Zobacz także

[Funkcje](../c-language/functions-c.md)
