---
title: Inicjowanie typów agregacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- aggregate types [C++]
- union keyword [C], declarations
- types [C], initializing
- union keyword [C]
- aggregates [C++], initializing
ms.assetid: a8f8ed75-39db-4592-93b9-d3920d915810
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c12ece1767c73e94551072532bfde6b36650bca9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="initializing-aggregate-types"></a>Inicjowanie typów agregacji
Typ "agregacji" jest struktura, Unią lub typ tablicy. Jeśli typ agregacji zawiera elementy członkowskie typów agregacji, rekursywnie zastosowanie zasady inicjowania.  
  
## <a name="syntax"></a>Składnia  
 *Inicjator*:  
 **{***listy inicjatorów***}** / * dla inicjowania agregacji \*/  
  
 **{***listy inicjatorów***,}**   
  
 *initializer-list*:  
 *initializer*  
  
 *Lista inicjalizatora***,***inicjatora*  
  
 *Listy inicjatorów* znajduje się lista inicjatory rozdzielonych przecinkami. Każdy na liście jest wyrażenie stałe lub listy inicjatorów. W związku z tym mogą być zagnieżdżane listy inicjatorów. Ten formularz jest przydatne w przypadku inicjowania agregacji elementów członkowskich typu agregacji, jak przedstawiono w przykładach w tej sekcji. Jednak jeśli inicjator dla identyfikatora automatyczne jedno wyrażenie, go nie musisz być wyrażeniem stałym; go jedynie musi mieć odpowiedni typ dla przypisania z identyfikatorem.  
  
 Dla każdej listy inicjalizatora stałej wyrażeń są przypisane wartości, w kolejności, odpowiednie elementy członkowskie agregacji zmiennej.  
  
 Jeśli *listy inicjatorów* ma mniejszą liczbę wartości niż typ agregacji, pozostałe elementy Członkowskie lub elementy typu agregacji są inicjowane na 0. Wartość początkowa automatyczne identyfikatora nie zostało zainicjowane jest niezdefiniowany. Jeśli *listy inicjatorów* ma więcej wartości niż typ agregacji, powoduje błąd. Te reguły mają zastosowanie do każdego inicjatora osadzonych listy, a także do agregacji jako całość.  
  
 Struktura inicjator jest wyrażenie tego samego typu lub listy inicjatorów dla jego elementów członkowskich ujętą w nawiasy klamrowe (**{}**). Nienazwane pole bitowe elementy członkowskie nie są zainicjowane.  
  
 Po zainicjowaniu Unii *listy inicjatorów* musi być pojedynczym wyrażeniem stałej. Wartość wyrażenia stałej jest przypisany do pierwszego elementu Członkowskiego Unii.  
  
 Jeśli tablica ma nieznany rozmiar, liczba inicjatory Określa rozmiar tablicy, a jego typ zostaje wykonane. Nie istnieje sposób określić powtarzania inicjatora w języku C lub zainicjować element środku tablicy nie oferuje również wszystkich powyższych wartości. Jeśli potrzebujesz tej operacji w programie, napisz rutynowych języka zestawu.  
  
 Należy pamiętać, że liczba inicjatorów może ustawiony rozmiar tablicy:  
  
```  
int x[ ] = { 0, 1, 2 }  
```  
  
 Określ rozmiar, nadaj niewłaściwą liczbę inicjatory jednak kompilator generuje błąd.  
  
 **Microsoft Specific**  
  
 Maksymalny rozmiar tablicy jest definiowana za pomocą **size_t**. Zdefiniowany w pliku nagłówka STDDEF. H, **size_t** jest `unsigned int` z zakresem 0x00000000 do 0x7CFFFFFF.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="examples"></a>Przykłady  
 Ten przykład przedstawia Inicjatory dla tablicy.  
  
```  
int P[4][3] =   
{  
    { 1, 1, 1 },  
    { 2, 2, 2 },  
    { 3, 3, 3,},  
    { 4, 4, 4,},  
};  
```  
  
 Ta instrukcja deklaruje `P` jako tablica czterech przez trzech i inicjuje elementy jego pierwszego wiersza do 1, elementy jej drugi wiersz 2, i tak dalej za pośrednictwem czwartego wiersza. Należy pamiętać, że na liście inicjatora dla wierszy trzeci i czwarty zawiera przecinkami po ostatnim wyrażenie stałe. Ostatni listy inicjatorów (`{4, 4, 4,},`) jest również rozdzielanych przecinkami. Te dodatkowe przecinkami są dozwolone, ale nie są wymagane; wymagane są tylko przecinkami wyrażenia stałe od siebie oraz te, które oddzielić od siebie, jedna lista inicjatora.  
  
 Jeśli zagregowany nie zawiera osadzonego inicjator listy, wartości są po prostu przypisywane, w kolejności, do każdego elementu członkowskiego subaggregate. W związku z tym inicjowania w poprzednim przykładzie jest odpowiednikiem następujące czynności:  
  
```  
int P[4][3] =   
{  
   1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4  
};  
```  
  
 Nawiasy klamrowe może również zostać wyświetlony wokół poszczególnych inicjatorów na liście i może pomóc w powyższym przykładzie wyjaśnienie.  
  
 Podczas inicjowania agregacji zmiennej, należy zachować ostrożność użyć nawiasów klamrowych inicjatora list i poprawnie. Poniższy przykład przedstawia interpretacji przez kompilator nawiasów klamrowych bardziej szczegółowo:  
  
```  
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
  
 W tym przykładzie `nlist` jest zadeklarowany jako tablica 2 przez 3 struktur, każda struktura o trzech elementów członkowskich. Wiersz 1 inicjowania przypisuje wartości do pierwszego wiersza `nlist`w następujący sposób:  
  
1.  Pierwszy lewy nawias klamrowy w wierszu 1 sygnały kompilator tego inicjowanie pierwszego członka łączny `nlist` (to znaczy `nlist[0]`) to początek.  
  
2.  Drugi lewego nawiasu klamrowego wskazuje tego inicjowanie pierwszego członka agregacji `nlist[0]` (to znaczy struktury na `nlist[0][0]`) to początek.  
  
3.  Inicjowanie struktury kończy się pierwszym prawy nawias klamrowy `nlist[0][0]`; dalej lewego nawiasu klamrowego rozpoczyna inicjowanie `nlist[0][1]`.  
  
4.  Proces jest kontynuowany do końca wiersza, w którym prawy nawias zamykający kończy się inicjowanie `nlist[0]`.  
  
 Wiersz 2 przypisuje wartości do drugiego wiersza `nlist` w podobny sposób. Należy pamiętać, że zestawy zewnętrzne nawiasów klamrowych otaczającej inicjatory w wierszach 1 i 2 są wymagane. Następujące konstrukcji pomija zewnętrzne nawiasów klamrowych, spowodowałoby błąd:  
  
```  
triplet nlist[2][3] =  /* THIS CAUSES AN ERROR */  
{  
     {  1, 2, 3 },{  4, 5, 6 },{  7, 8, 9 },   /* Line 1 */  
     { 10,11,12 },{ 13,14,15 },{ 16,17,18 }    /* Line 2 */  
};  
```  
  
 W tej konstrukcji pierwszy lewy nawias klamrowy w wierszu nr 1 rozpoczyna inicjowanie `nlist[0]`, czyli tablicę trzy struktury. Trzy elementy członkowskie struktury pierwszy są przypisane wartości 1, 2 i 3. Gdy dalej prawy nawias klamrowy jest napotkano (po wartości 3), inicjowanie `nlist[0]` zostanie zakończone, a dwie pozostałe struktury w tablicy trzech struktury są automatycznie inicjowane na 0. Podobnie `{ 4,5,6 }` inicjuje pierwszy struktury w drugim wierszu `nlist`. Pozostałe dwie struktury `nlist[1]` są ustawione na 0. Gdy kompilator napotka dalej listy inicjatorów ( `{ 7,8,9 }` ), próbuje zainicjować `nlist[2]`. Ponieważ `nlist` ma tylko dwa wiersze, ta próba spowoduje wystąpienie błędu.  
  
 W tym przykładzie dalej trzech `int` członkami `x` są inicjowane odpowiednio do 1, 2 i 3.  
  
```  
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
  
 W `list` struktury powyżej, trzy elementy w pierwszym wierszu `m` są inicjowane 4.0; elementy pozostałych wiersza `m` są inicjowane 0,0 domyślnie.  
  
```  
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
  
 Zmienna Unii `y`, w tym przykładzie został zainicjowany. Pierwszy element Unii jest tablicą, więc jest inicjator agregacji. Na liście inicjatora `{'1'}` przypisuje wartości do pierwszego wiersza tabeli. Ponieważ tylko jedną wartość znajduje się na liście, w pierwszej kolumnie elementu jest inicjowana na znak `1`, a pozostałe dwa elementy w wierszu są ustawiana na wartość 0, domyślnie. Podobnie, pierwszy element drugi wiersz `x` jest inicjowana na znak `4`, a pozostałe dwa elementy w tym wierszu są inicjowane na wartość 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjowanie](../c-language/initialization.md)