---
title: Deklaracje złożeń
ms.date: 11/04/2016
helpviewer_keywords:
- unions
- union keyword [C], declarations
- variant records
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
ms.openlocfilehash: 3414a478ec741351f1e1540a214cca38c029749f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213700"
---
# <a name="union-declarations"></a>Deklaracje złożeń

"Deklaracja Unii" określa zestaw wartości zmiennych i, opcjonalnie, oznakowanie nazwy Unii. Zmienne wartości są nazywane "składowymi" Unii i mogą mieć różne typy. Unii są podobne do "rekordów wariantów" w innych językach.

## <a name="syntax"></a>Składnia

*specyfikator struct-or-Union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<sub>wybór</sub> *identyfikatora* *struct-or-Union* **{** *struct-deklaracji-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator* *struktury lub Unii*

*struct-lub-Union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`struct`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`union`**

*Struktura-deklaracja-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura — deklaracja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Struktura *-Deklaracja list* — *Deklaracja*

Zawartość Union jest definiowana jako

*Deklaracja struktury*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikator-kwalifikator list* - *deklarator-list*  **;**

*specyfikator — lista kwalifikatorów*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Specyfikator *typu specyfikatora* - *kwalifikator —*<sub>wybór</sub> listy <br/>
&nbsp;&nbsp;&nbsp;&nbsp;Specyfikator *kwalifikatora typu* —<sub>wybór</sub> *listy*

*struct-deklarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura — deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-deklarator-list*  **,**  *struct-deklarator*

Zmienna z **`union`** typem przechowuje jedną z wartości zdefiniowanych przez ten typ. Te same reguły regulują strukturę i deklaracje Unii. Unie mogą również zawierać pola bitowe.

Elementy członkowskie Unii nie mogą mieć niekompletnego typu, typu **`void`** lub typu funkcji. W związku z tym elementy członkowskie nie mogą być wystąpieniem Unii, ale mogą być wskaźnikami do zadeklarowanego typu złożenia.

Deklaracja typu Union jest tylko szablonem. Pamięć nie jest zarezerwowana do momentu zadeklarowania zmiennej.

> [!NOTE]
> Jeśli jest zadeklarowana Unia dwóch typów i jest przechowywana jedna wartość, a Unia jest dostępna z innym typem, wyniki są niezawodne. Na przykład Unia **`float`** i **`int`** jest zadeklarowana. **`float`** Wartość jest przechowywana, ale program później uzyskuje dostęp do wartości jako **`int`** . W takiej sytuacji wartość będzie zależeć od wewnętrznego magazynu **`float`** wartości. Wartość całkowita nie będzie godna zaufania.

## <a name="examples"></a>Przykłady

Poniżej przedstawiono przykłady Unii:

```C
union sign   /* A definition and a declaration */
{
    int svar;
    unsigned uvar;
} number;
```

W tym przykładzie zdefiniowano zmienną Union z `sign` typem i deklaruje zmienną o nazwie `number` , która ma dwie składowe: `svar` , liczbę całkowitą ze znakiem i `uvar` , liczbę całkowitą bez znaku. Ta deklaracja umożliwia przechowywanie bieżącej wartości `number` jako wartości ze znakiem lub bez znaku. Tag skojarzony z tym typem Unii to `sign` .

```C
union               /* Defines a two-dimensional */
{                   /*  array named screen */
    struct
    {
      unsigned int icon : 8;
      unsigned color : 4;
    } window1;
    int screenval;
} screen[25][80];
```

`screen`Tablica zawiera 2 000 elementów. Każdy element tablicy jest pojedynczym złożeniem z dwoma elementami członkowskimi: `window1` i `screenval` . `window1`Składowa jest strukturą zawierającą dwa elementy członkowskie pola bitowego `icon` i `color` . `screenval`Element członkowski jest **`int`** . W danym momencie każdy element Union posiada **`int`** reprezentowane przez `screenval` lub strukturę reprezentowane przez `window1` .

**Specyficzne dla firmy Microsoft**

W przypadku, gdy są elementami członkowskimi innej struktury lub Unii, można zadeklarować je anonimowo. Jest to przykład Unii pustego:

```C
struct str
{
    int a, b;
    union            / * Unnamed union */
    {
      char c[4];
      long l;
      float f;
   };
   char c_array[10];
} my_str;
.
.
.
my_str.l == 0L;  /* A reference to a field in the my_str union */
```

Unii są często zagnieżdżane w strukturze, która zawiera pole, w którym dane są zawarte w Unii w określonym czasie. Jest to przykład deklaracji dla takiej Unii:

```C
struct x
{
    int type_tag;
    union
    {
      int x;
      float y;
    }
}
```

Zobacz [struktury i składowe Unii,](../c-language/structure-and-union-members.md) Aby uzyskać informacje dotyczące przywołujących się do nich związków.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)
