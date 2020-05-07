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
ms.openlocfilehash: f6816a6f63de262b927a3c5aeed8774ba29c2eaa
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "62326082"
---
# <a name="initializing-aggregate-types"></a>Inicjowanie typów agregacji

Typ *zagregowany* jest strukturą, Unią lub typem tablicy. Jeśli typ agregacji zawiera elementy członkowskie typów agregacji, reguły inicjalizacji są stosowane cyklicznie.

## <a name="syntax"></a>Składnia

*inicjator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{**  *inicjator-list*  **}** /* do zainicjowania agregacji\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{**  *inicjator — lista*  **,}**

*Lista inicjalizatora*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*skład*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inicjator — lista*  **,**  *inicjator*

*Lista inicjalizatora* jest listą inicjatorów rozdzielonych przecinkami. Każdy inicjator na liście jest wyrażeniem stałym lub listą inicjatorów. W związku z tym listy inicjatorów mogą być zagnieżdżane. Ten formularz jest przydatny do inicjowania agregowanych elementów członkowskich typu agregacji, jak pokazano w przykładach w tej sekcji. Jeśli jednak inicjator dla automatycznego identyfikatora jest pojedynczym wyrażeniem, nie musi być wyrażeniem stałym; tylko musi mieć odpowiedni typ do przypisywania do identyfikatora.

Dla każdej listy inicjatora wartości wyrażeń stałych są przypisywane w kolejności do odpowiednich elementów członkowskich zmiennej agregującej.

Jeśli *inicjator-lista* ma mniejszą liczbę wartości niż typ zagregowany, pozostałe elementy członkowskie lub elementy typu agregacji są inicjowane do wartości 0. Początkowa wartość automatycznego identyfikatora, który nie został jawnie zainicjowany jest niezdefiniowana. Jeśli *inicjator — lista* zawiera więcej wartości niż typ zagregowany, wyniki błędu. Te reguły mają zastosowanie do każdej listy osadzonych inicjatorów, a także do agregacji jako całości.

Inicjator struktury jest wyrażeniem tego samego typu lub listą inicjatorów elementów członkowskich ujętych w nawiasy klamrowe (**{}**). Nienazwane elementy członkowskie pola bitowego nie są inicjowane.

Gdy Unia zostanie zainicjowana, *Lista inicjatorów* musi być wyrażeniem o pojedynczej stałej. Wartość wyrażenia stałego jest przypisywana do pierwszego elementu członkowskiego Unii.

Jeśli tablica ma nieznany rozmiar, liczba inicjatorów określa rozmiar tablicy, a jej typ zostanie ukończony. Nie ma możliwości określenia powtórzenia inicjatora w języku C lub zainicjowania elementu w środku tablicy bez podawania wszystkich poprzednich wartości. Jeśli potrzebujesz tej operacji w programie, napisz procedurę w języku asemblera.

Należy zauważyć, że liczba inicjatorów może ustawić rozmiar tablicy:

```C
int x[ ] = { 0, 1, 2 }
```

Jeśli określisz rozmiar i podasz nieprawidłową liczbę inicjatorów, kompilator generuje błąd.

**Specyficzne dla firmy Microsoft**

Maksymalny rozmiar tablicy jest definiowany przez **size_t**. Zdefiniowane w pliku nagłówka STDDEF. H, **size_t** jest `unsigned int` z zakresem od 0x00000000 do 0x7CFFFFFF.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="examples"></a>Przykłady

Ten przykład pokazuje inicjatory dla tablicy.

```C
int P[4][3] =
{
    { 1, 1, 1 },
    { 2, 2, 2 },
    { 3, 3, 3,},
    { 4, 4, 4,},
};
```

Ta instrukcja deklaruje `P` jako tablicę czterech przez trzy i inicjuje elementy pierwszego wiersza do 1, elementy z drugiego wiersza do 2 i tak dalej w czwartym wierszu. Należy zauważyć, że lista inicjatorów dla trzeciego i czwartego wiersza zawiera przecinki po ostatnim wyrażeniu stałej. Po ostatniej liście inicjatora`{4, 4, 4,},`() występuje również przecinek. Te dodatkowe przecinki są dozwolone, ale nie są wymagane; wymagane są tylko przecinki, które oddzielają wyrażenia stałe od siebie i te, które oddzielają jedną listę inicjatorów od innych.

Jeśli zagregowany element członkowski nie ma osadzonej listy inicjatorów, wartości są po prostu przypisywane do każdego elementu członkowskiego agregacji. W związku z tym Inicjalizacja w poprzednim przykładzie jest równoważna z następującymi:

```C
int P[4][3] =
{
   1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4
};
```

Nawiasy klamrowe mogą również znajdować się na poszczególnych inicjatorach listy i pomóc w wyjaśnieniu powyższego przykładu.

Po zainicjowaniu zmiennej agregującej należy zachować ostrożność, aby prawidłowo używać nawiasów klamrowych i list inicjatorów. Poniższy przykład ilustruje interpretację nawiasów klamrowych w bardziej szczegółowy sposób:

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

W tym przykładzie `nlist` jest zadeklarowana jako tablica o strukturze 2-by-3, każda struktura ma trzy składowe. Wiersz 1 inicjalizacji przypisuje wartości do pierwszego wiersza `nlist`w następujący sposób:

1. Pierwszy lewy nawias klamrowy w wierszu 1 sygnalizuje kompilator inicjujący pierwszy zagregowany element członkowski `nlist` (czyli, `nlist[0]`).

1. Drugi lewy nawias klamrowy wskazuje, że inicjalizacja pierwszego zagregowanego elementu `nlist[0]` członkowskiego (czyli struktury w `nlist[0][0]`) zaczyna się.

1. Pierwszy prawy nawias klamrowy zamyka inicjalizację struktury `nlist[0][0]`; Następny lewy nawias klamrowy zaczyna inicjalizację `nlist[0][1]`.

1. Proces jest kontynuowany do końca wiersza, gdzie zamykający się prawy nawias klamrowy kończy inicjalizację `nlist[0]`.

Wiersz 2 przypisuje wartości do drugiego wiersza `nlist` w podobny sposób. Należy zauważyć, że zewnętrzne zestawy nawiasów klamrowych otaczających inicjatory w wierszach 1 i 2 są wymagane. Następująca konstrukcja, która pomija zewnętrzne nawiasy klamrowe, spowoduje wystąpienie błędu:

```C
triplet nlist[2][3] =  /* THIS CAUSES AN ERROR */
{
     {  1, 2, 3 },{  4, 5, 6 },{  7, 8, 9 },   /* Line 1 */
     { 10,11,12 },{ 13,14,15 },{ 16,17,18 }    /* Line 2 */
};
```

W tej konstrukcji pierwszy lewy nawias klamrowy w wierszu 1 zaczyna inicjalizację `nlist[0]`, która jest tablicą trzech struktur. Wartości 1, 2 i 3 są przypisywane do trzech członków pierwszej struktury. Po napotkaniu następnego prawego nawiasu klamrowego (po wartości 3) Inicjalizacja `nlist[0]` jest zakończona, a dwie pozostałe struktury w tablicy z trzema strukturami są automatycznie inicjowane na wartość 0. Podobnie, `{ 4,5,6 }` inicjuje pierwszą strukturę w drugim wierszu `nlist`. Pozostałe dwie struktury `nlist[1]` są ustawione na 0. Gdy kompilator napotka następną listę inicjatora ( `{ 7,8,9 }` ), próbuje zainicjować. `nlist[2]` Ponieważ `nlist` ma tylko dwa wiersze, ta próba powoduje błąd.

W tym następnym przykładzie trzy `int` elementy członkowskie `x` są inicjowane odpowiednio do wartości 1, 2 i 3.

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

W powyższej `list` strukturze trzy elementy w pierwszym wierszu `m` są inicjowane do 4,0; elementy pozostałego wiersza `m` są domyślnie inicjowane do 0,0.

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

W tym przykładzie `y`zmienna Union jest inicjowana. Pierwszy element Unii jest tablicą, więc inicjator jest inicjatorem agregującym. Lista `{'1'}` inicjatora przypisuje wartości do pierwszego wiersza tablicy. Ponieważ na liście jest wyświetlana tylko jedna wartość, element w pierwszej kolumnie jest inicjowany do znaku `1`, a pozostałe dwa elementy w wierszu są domyślnie inicjowane do wartości 0. Podobnie pierwszy element drugiego wiersza `x` jest inicjowany do znaku `4`, a pozostałe dwa elementy w wierszu są inicjowane do wartości 0.

## <a name="see-also"></a>Zobacz też

[Inicjowanie](../c-language/initialization.md)
