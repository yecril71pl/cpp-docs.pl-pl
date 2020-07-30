---
title: Deklaracje struktur
ms.date: 11/04/2016
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
ms.openlocfilehash: 3b9aa30cfeecbd60fda61e6a484043c82c9a3b28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217054"
---
# <a name="structure-declarations"></a>Deklaracje struktur

"Deklaracja struktury" nazywa typ i określa sekwencję wartości zmiennych (nazywany "składowymi" lub "pola" struktury), które mogą mieć różne typy. Opcjonalny identyfikator o nazwie "tag" daje nazwę typu struktury i może być używany w kolejnych odwołaniach do typu struktury. Zmienna tego typu struktury zawiera całą sekwencję zdefiniowaną przez ten typ. Struktury w języku C są podobne do typów znanych jako "Records" w innych językach.

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

*Deklaracja struktury*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikator-kwalifikator list* - *deklarator-list* **;**

*specyfikator — lista kwalifikatorów*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Specyfikator *typu specyfikatora* - *kwalifikator —*<sub>wybór</sub> listy<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Specyfikator *kwalifikatora typu* —<sub>wybór</sub> *listy*

*struct-deklarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-deklarator* *struct-deklarator-list* **,** *struct-deklarator*

*Struktura-deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typ-specyfikator* *deklarator*<sub>opt</sub> **:** *wyrażenie stałe*

Deklaracja typu struktury nie ustawia miejsca na przestrzeń dla struktury. Jest to tylko szablon do późniejszej deklaracji zmiennych struktury.

Wcześniej zdefiniowany *Identyfikator* (tag) może służyć do odwoływania się do typu struktury zdefiniowanego w innym miejscu. W tym przypadku nie można powtórzyć *listy deklaracji struktury* , dopóki definicja jest widoczna. Deklaracje wskaźników do struktur i elementów typedef dla typów struktury mogą używać znacznika struktury przed zdefiniowaniem typu struktury. Jednak Definicja struktury musi zostać wykryty przed rzeczywistym użyciem rozmiaru pól. Jest to niepełna definicja typu i znacznika typu. Aby można było ukończyć tę definicję, definicja typu musi pojawić się w dalszej części tego samego zakresu.

*Deklaracja struktury-list* określa typy i nazwy elementów członkowskich struktury. Argument *listy deklaracji struktury* zawiera co najmniej jedną deklarację zmiennej lub pola bitowego.

Każda zmienna zadeklarowana na *liście struktury deklaracji* jest definiowana jako element członkowski typu struktury. Deklaracje zmiennych w ramach *listy deklaracji struktury* mają taki sam formularz jak inne deklaracje zmiennych omówione w tej sekcji, z tą różnicą, że deklaracje nie mogą zawierać specyfikatorów klasy magazynu ani inicjatorów. Elementy członkowskie struktury mogą mieć dowolne typy zmiennych, z wyjątkiem typu **`void`** , niekompletnego typu lub typu funkcji.

Składowej nie można zadeklarować jako typu struktury, w której występuje. Jednakże element członkowski może być zadeklarowany jako wskaźnik do typu struktury, w którym występuje tak długo, jak typ struktury ma tag. Pozwala to na tworzenie połączonych list struktur.

Struktury są zgodne z tym samym zakresem co inne identyfikatory. Identyfikatory struktury muszą być różne od innych tagów struktury, Unii i wyliczenia o tej samej widoczności.

Każda *Deklaracja struktury* na *liście struktur deklaracji* musi być unikatowa w obrębie listy. Jednak nazwy identyfikatorów na *liście deklaracji struktury* nie muszą być różne od zwykłych nazw zmiennych lub z identyfikatorów w innych listach deklaracji struktury.

Zagnieżdżone struktury można także uzyskać, gdy zostały zadeklarowane na poziomie pliku. Na przykład, dana deklaracja:

```C
struct a
{
    int x;
    struct b
    {
      int y;
    } var2;
} var1;
```

te deklaracje są zarówno prawne:

```C
struct a var3;
struct b var4;
```

## <a name="examples"></a>Przykłady

Te przykłady ilustrują deklaracje struktury:

```C
struct employee   /* Defines a structure variable named temp */
{
    char name[20];
    int id;
    long class;
} temp;
```

`employee`Struktura ma trzy elementy członkowskie: `name` , `id` , i `class` . `name`Składowa jest 20-elementową tablicą i `id` i `class` są prostymi elementami członkowskimi z **`int`** i **`long`** typu, odpowiednio. Identyfikator `employee` jest identyfikatorem struktury.

```C
struct employee student, faculty, staff;
```

W tym przykładzie zdefiniowano trzy zmienne struktury: `student` , `faculty` , i `staff` . Każda struktura ma tę samą listę trzech elementów członkowskich. Elementy członkowskie są zadeklarowane jako mają typ struktury `employee` zdefiniowany w poprzednim przykładzie.

```C
struct           /* Defines an anonymous struct and a */
{                /* structure variable named complex  */
    float x, y;
} complex;
```

`complex`Struktura ma dwa elementy członkowskie **`float`** typu, `x` i `y` . Typ struktury nie ma tagu i w związku z tym jest nienazwany lub anonimowy.

```C
struct sample   /* Defines a structure named x */
{
    char c;
    float *pf;
    struct sample *next;
} x;
```

Pierwsze dwa elementy członkowskie struktury są **`char`** zmienną i wskaźnikiem do **`float`** wartości. Trzeci członek, `next` ,, jest zadeklarowany jako wskaźnik do zdefiniowanego typu struktury ( `sample` ).

Struktury anonimowe mogą być przydatne, gdy tag o nazwie nie jest wymagany. Jest to przypadek, gdy jedna deklaracja definiuje wszystkie wystąpienia struktury. Na przykład:

```C
struct
{
    int x;
    int y;
} mystruct;
```

Osadzone struktury są często anonimowe.

```C
struct somestruct
{
    struct    /* Anonymous structure */
    {
        int x, y;
    } point;
    int type;
} w;
```

**Specyficzne dla firmy Microsoft**

Kompilator umożliwia tablicę o rozmiarze niezmienionym lub zerowym jako ostatni element członkowski struktury. Może to być przydatne, jeśli rozmiar tablicy stałej jest różny, gdy jest używany w różnych sytuacjach. Deklaracja takiej struktury wygląda następująco:

**`struct`***Identyfikator* **{** *zestaw deklaracji* *typu* <em>Array-Name</em>** \[ ];};**

Tablice bez rozmiaru mogą występować tylko jako ostatni element członkowski struktury. Struktury zawierające deklaracje tablic bez rozmiaru mogą być zagnieżdżane w innych strukturach, o ile nie są zadeklarowane dalsze składowe w żadnej z otaczających struktur. Tablice takich struktur są niedozwolone. **`sizeof`** Operator, gdy jest stosowany do zmiennej tego typu lub samego typu, przyjmuje wartość 0 dla rozmiaru tablicy.

Deklaracje struktury można także określić bez elementu deklarator, gdy są one elementami członkowskimi innej struktury lub Unii. Nazwy pól są podwyższane do otaczającej struktury. Na przykład struktura pustego wygląda następująco:

```C
struct s
{
    float y;
    struct
    {
        int a, b, c;
    };
    char str[10];
} *p_s;
.
.
.
p_s->b = 100;  /* A reference to a field in the s structure */
```

Aby uzyskać informacje o odwołaniach do struktury [, zobacz Struktura i składowe Unii](../c-language/structure-and-union-members.md) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)
