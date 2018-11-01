---
title: Inicjowanie typów agregacji
ms.date: 11/04/2016
helpviewer_keywords:
- aggregate types [C++]
- union keyword [C], declarations
- types [C], initializing
- union keyword [C]
- aggregates [C++], initializing
ms.assetid: a8f8ed75-39db-4592-93b9-d3920d915810
ms.openlocfilehash: ebc7f6185c8115df6e6b77a034307f8998b1c2ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530311"
---
# <a name="initializing-aggregate-types"></a>Inicjowanie typów agregacji

*Agregacji* typem jest struktura, Unia lub typu tablicowego. Jeśli typem agregowanym zawiera składowych typu agregacji, mają zastosowanie reguły inicjowania cyklicznie.

## <a name="syntax"></a>Składnia

*Inicjator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{***listy inicjatorów***}** / * dla inicjowania agregacji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{***listy inicjatorów***,}**

*initializer-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Inicjator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*listy inicjatorów***,***inicjatora*

*Listy inicjatorów* znajduje się lista inicjatorów rozdzielonych przecinkami. Każdego inicjatora na liście jest wyrażeniem stałym lub listy inicjalizatora. W związku z tym można zagnieżdżać listy inicjatorów. Ten formularz jest przydatne w przypadku inicjowanie agregacji elementów członkowskich typu agregacji, jak pokazano w przykładach w tej sekcji. Jednak jeśli inicjator dla automatycznemu identyfikatorowi jest pojedyncze wyrażenie, go nie musi być wyrażeniem stałym; jedynie musi ona mieć odpowiedni typ w celu przypisania do identyfikatora.

Dla każdej listy inicjatorów wartości wyrażenia stałe są przypisane, w kolejności, do odpowiednich elementów członkowskich zmiennej agregacji.

Jeśli *listy inicjatorów* zawiera mniej niż odpowiedni typ agregacji, pozostałe elementy Członkowskie lub elementy odpowiedni typ agregacji są inicjowane na wartość 0. Początkowa wartość identyfikatora automatyczne nie zostały jawnie zainicjować jest niezdefiniowane. Jeśli *listy inicjatorów* ma więcej wartości niż odpowiedni typ agregacji, powoduje błąd. Te reguły mają zastosowanie do każdej listy inicjatora osadzonych, a także do agregacji jako całości.

Struktura inicjator jest wyrażenia tego samego typu lub listy inicjatorów dla jego elementów członkowskich, ujęte w nawiasy klamrowe (**{}**). Nienazwane elementy członkowskie pole bitowe nie są inicjowane.

Podczas inicjowania Unii *listy inicjatorów* musi być pojedynczym wyrażeniem stałej. Wartość wyrażenie stałe jest przypisana do pierwszego elementu Członkowskiego Unii.

Jeśli tablica ma nieznany rozmiar, liczba inicjatorów Określa rozmiar tablicy, a jego typ zostaje wykonane. Nie istnieje sposób określić powtórzenia inicjatora w języku C lub zainicjować element w środku tablicy bez podawania również wszystkie poprzedniej wartości. Jeśli potrzebujesz tej operacji w programie zapisu procedura w języku zestawu.

Należy zwrócić uwagę na to, że liczba inicjatorów można ustawić rozmiar tablicy:

```C
int x[ ] = { 0, 1, 2 }
```

Jeśli określić rozmiar i nadaj niewłaściwą liczbę inicjatory, jednak kompilator generuje błąd.

**Microsoft Specific**

Maksymalny rozmiar tablicy jest definiowany przez **size_t**. Zdefiniowane w pliku nagłówkowym STDDEF. Godz., **size_t** jest `unsigned int` z zakresem 0x00000000 do 0x7CFFFFFF.

**END specyficzny dla Microsoft**

## <a name="examples"></a>Przykłady

Ten przykład przedstawia inicjatorów dla tablic.

```C
int P[4][3] =
{
    { 1, 1, 1 },
    { 2, 2, 2 },
    { 3, 3, 3,},
    { 4, 4, 4,},
};
```

Ta instrukcja deklaruje `P` jako tablicę czterech 3 i inicjuje elementy jej pierwszy wiersz 1, elementy jego drugi wiersz 2 i tak dalej za pośrednictwem czwartym wierszu. Należy pamiętać, że na liście inicjatora dla wierszy trzecia i czwarta zawiera przecinki po ostatnim wyrażenie stałe. Ostatnie lista inicjatora (`{4, 4, 4,},`) jest również rozdzielanych przecinkami. Te dodatkowe przecinkami są dozwolone, ale nie są wymagane; tylko przecinki oddzielające wyrażenia stałe od siebie nawzajem i tych, które oddzielić jednej listy inicjatorów od innego, są wymagane.

Jeśli zagregowany nie zawiera osadzonego inicjatora listy, wartości są po prostu przypisywane, w kolejności, do każdego członka subaggregate. W związku z tym inicjowania w poprzednim przykładzie jest odpowiednikiem następujących czynności:

```C
int P[4][3] =
{
   1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4
};
```

Nawiasów może również zostać wyświetlony wokół poszczególne inicjatory na liście i może pomóc w wyjaśnieniu w powyższym przykładzie.

Podczas inicjowania zmiennej agregacji, należy zachować ostrożność użyć nawiasów klamrowych i inicjatora wyświetla prawidłowo. Poniższy przykład ilustruje kompilatora interpretacji nawiasów klamrowych bardziej szczegółowo:

```C
typedef struct
{
    int n1, n2, n3;
} triplet;

triplet nlist[2][3] =
{
    { {  1, 2, 3 }, {  4, 5, 6 }, {  7, 8, 9 } },  /* Row 1 */
    { { 10,11,12 }, { 13,14,15 }, { 16,17,18 } }   /* Row 2 */
};
```

W tym przykładzie `nlist` jest zadeklarowana jako tablica 2, 3, struktur, każda struktura o trzy elementy członkowskie. Wiersz 1 inicjowania przypisuje wartości do pierwszego wiersza `nlist`, wykonując następujące czynności:

1. Pierwszy lewy nawias klamrowy w wierszu 1 sygnalizuje kompilator, że inicjowanie pierwszego agregacji elementu członkowskiego `nlist` (czyli `nlist[0]`) to początek.

1. Drugi nawias klamrowy otwierający wskazuje, że inicjowanie pierwszego agregacji elementu członkowskiego `nlist[0]` (czyli struktury na `nlist[0][0]`) to początek.

1. Pierwszy nawias klamrowy zamykający kończy inicjowania struktury `nlist[0][0]`; dalej nawias klamrowy otwierający rozpoczyna inicjowanie `nlist[0][1]`.

1. Proces jest kontynuowany aż do końca wiersza, w którym zamykający nawias klamrowy zamykający kończy się inicjowanie `nlist[0]`.

Wiersz 2 przypisuje wartości do drugiego wiersza `nlist` w podobny sposób. Należy pamiętać, że zestawy zewnętrzne w nawiasy klamrowe obejmujące inicjatory w wierszach 1 i 2 są wymagane. Następujące konstrukcji, pomija zewnętrzne nawiasów klamrowych, spowodowałoby błąd:

```C
triplet nlist[2][3] =  /* THIS CAUSES AN ERROR */
{
     {  1, 2, 3 },{  4, 5, 6 },{  7, 8, 9 },   /* Line 1 */
     { 10,11,12 },{ 13,14,15 },{ 16,17,18 }    /* Line 2 */
};
```

W tej konstrukcji pierwszy lewy nawias klamrowy w wierszu 1 rozpoczyna się inicjowanie `nlist[0]`, które jest tablicą trzy struktury. Trzy elementy członkowskie struktury pierwszego są przypisane wartości 1, 2 i 3. Po następnym nawias klamrowy zamykający napotkano (po wartość 3), inicjowanie `nlist[0]` zostanie zakończone, a dwie pozostałe struktury, w tablicy struktury trzy automatycznie jest inicjowana wartością 0. Podobnie `{ 4,5,6 }` inicjuje pierwszy struktury w drugim wierszu `nlist`. Pozostałe dwie struktury z `nlist[1]` są ustawione na 0. Gdy kompilator napotka na następnej liście inicjatora ( `{ 7,8,9 }` ), próbuje zainicjować `nlist[2]`. Ponieważ `nlist` ma tylko dwa wiersze, ta próba spowoduje wystąpienie błędu.

W tym przykładzie dalej trzy `int` członkowie `x` są inicjowane na wartość 1, 2 i 3, odpowiednio.

```C
struct list
{
    int i, j, k;
    float m[2][3];
} x = {
        1,
        2,
        3,
       {4.0, 4.0, 4.0}
      };
```

W `list` struktury powyżej, trzy elementy w pierwszym wierszu `m` są inicjowane na wartość 4.0; elementy pozostałe wiersza `m` są inicjowane na wartość 0,0 domyślnie.

```C
union
{
    char x[2][3];
    int i, j, k;
} y = { {
            {'1'},
            {'4'}
        }
      };
```

Zmienna złożenia `y`, w tym przykładzie jest zainicjowany. Pierwszy element Unii jest tablicą, więc inicjator jest inicjatorów agregacji. Na liście inicjatora `{'1'}` przypisuje wartości do pierwszego wiersza w tablicy. Ponieważ tylko jedną wartość pojawia się na liście, element w pierwszej kolumnie jest inicjowany do znaku `1`, a pozostałe dwa elementy w wierszu są inicjowane na wartość 0, domyślnie. Podobnie, pierwszy element drugiego wiersza `x` jest inicjowany do znaku `4`, a pozostałe dwa elementy w tym wierszu są inicjowane na wartość 0.

## <a name="see-also"></a>Zobacz też

[Inicjowanie](../c-language/initialization.md)