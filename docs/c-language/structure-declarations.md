---
title: Deklaracje struktury | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2448a34f85ab33c1a8d587b0eb44530e5e2417a7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754049"
---
# <a name="structure-declarations"></a>Deklaracje struktur
"Deklaracji struktury" nazwy typu i określa sekwencję wartości zmiennych (nazywany "Członkowie" lub "fields" struktury), które mogą mieć różne typy. Opcjonalny identyfikator o nazwie "tag", nadaje nazwę typu struktury i mogą być używane w kolejnych odwołaniach do typu struktury. Zmienna tego typu struktury zawiera całą sekwencję zdefiniowane według tego typu. Struktury w języku C są podobne do typów, znane jako "rekordy" w innych językach.  
  
## <a name="syntax"></a>Składnia

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struktury lub Unii* *identyfikator*<sub>zoptymalizowany pod kątem</sub> **{** *struktury deklaracji listy* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struktury lub Unii* *identyfikator*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**— Struktura**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Unia**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja — struktura*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura deklaracji listy* *deklaracji struktury*

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator kwalifikator listy* *struktury declarator-list* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikator kwalifikator listy*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikator kwalifikator listy*<sub>zoptymalizowany pod kątem</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura declarator* *struktury declarator-list* **,** *deklaratora — struktura*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *deklaratora*<sub>zoptymalizowany pod kątem</sub> **:** *wyrażenia stałego*
  
Deklaracja typu struktury Nieustawione zarezerwować miejsce dla struktury. Jest tylko szablon służący do nowszych deklaracje zmiennych struktury.  
  
A uprzednio zdefiniowany *identyfikator* (tagów) może służyć do odwoływania się do typ struktury zdefiniowany w innym miejscu. W tym przypadku *struktury deklaracji listy* nie może powtarzać tak długo, jak definicja jest widoczny. Deklaracje wskaźników do struktur i definicje typów dla typów struktury, można użyć tag struktury, przed zdefiniowaniem typ struktury. Jednak definicji struktury musi napotkał przed jakimkolwiek użyciem rzeczywisty rozmiar pól. Jest niekompletna definicja typu oraz tag typu. Dla tej definicji, należy wykonać definicja typu musi znajdować się w dalszej części w tym samym zakresie.  
  
*Struktury deklaracji listy* Określa typy i nazwy elementów członkowskich struktury. A *struktury deklaracji listy* argument zawiera co najmniej jednej zmiennej lub deklaracje pole bitowe.  
  
Każda Zmienna zadeklarowana w *struktury deklaracji listy* jest zdefiniowany jako członek typu struktury. Deklaracje zmiennych w ramach *struktury deklaracji listy* mają tę samą postać co innych deklaracji zmiennych, które zostały omówione w tej sekcji, z tą różnicą, że deklaracje nie może zawierać specyfikatory klasy magazynowania lub inicjatorów. Elementy członkowskie struktury mogą mieć wszystkie typy zmiennych, z wyjątkiem typu `void`, typu niekompletnego lub typu funkcji.  
  
Nie można zadeklarować członek typ struktury, w której występuje. Jednak członka może być deklarowana jako wskaźnik do struktury typu, w której występuje tak długo, jak typ struktury ma tag. Dzięki temu można utworzyć połączonej listy struktur.  
  
Struktury postępuj zgodnie z tego samego zakresu jak innych identyfikatorów. Struktura identyfikatory muszą być różne od innych struktury, Unii i wyliczenia tagi z taką samą widoczność.  
  
Każdy *deklaracji struktury* w *struktury deklaracji listy* muszą być unikatowe w obrębie listy. Jednak identyfikatora nazwy w *struktury deklaracji listy* nie muszą się różnić od zwykłej nazwy zmiennych lub z identyfikatorów w inne listy deklaracji struktury.  
  
Zagnieżdżone struktury można również uzyskać dostęp, tak, jakby były one zadeklarowane na poziomie zakresu pliku. Na przykład biorąc pod uwagę tę deklarację:  
  
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
  
Deklaracje te są prawne:  
  
```C
struct a var3;  
struct b var4;  
```  
  
## <a name="examples"></a>Przykłady  
Te przykłady ilustrują deklaracje struktur:  
  
```C
struct employee   /* Defines a structure variable named temp */  
{  
    char name[20];  
    int id;  
    long class;  
} temp;  
```  
  
`employee` Struktura ma trzy elementy członkowskie: `name`, `id`, i `class`. `name` Element członkowski jest 20-elementowej tablicy, i `id` i `class` są proste członków z `int` i **długie** typ, odpowiednio. Identyfikator `employee` jest identyfikatorem struktury.  
  
```C
struct employee student, faculty, staff;  
```  
  
Ten przykład definiuje trzy zmienne struktury: `student`, `faculty`, i `staff`. Każda struktura została ta sama lista trzy elementy członkowskie. Elementy członkowskie są zadeklarowane typ struktury `employee`zdefiniowaną w poprzednim przykładzie.  
  
```C
struct           /* Defines an anonymous struct and a */  
{                /* structure variable named complex  */  
    float x, y;  
} complex;  
```  
  
`complex` Struktura ma dwa elementy członkowskie z **float** typu `x` i `y`. Typ struktury nie ma tagu i dlatego nienazwane lub anonimowe.  
  
```C
struct sample   /* Defines a structure named x */  
{  
    char c;  
    float *pf;  
    struct sample *next;  
} x;  
```  
  
Pierwsze dwa elementy członkowskie struktury są `char` zmiennej i wskaźnik **float** wartość. Trzeci członek `next`, jest zadeklarowany jako wskaźnik do typu struktury definiowanego (`sample`).  
  
Struktury anonimowe może być przydatne, gdy tag o nazwie nie jest potrzebne. Dotyczy to sytuacji, gdy jedna deklaracja określa wszystkie wystąpienia struktury. Na przykład:  
  
```C
struct  
{  
    int x;  
    int y;  
} mystruct;  
```  
  
Struktury osadzone często są anonimowe.  
  
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
  
**Microsoft Specific**  
  
Kompilator umożliwi tablica bez określonego rozmiaru lub o rozmiarze zero jako ostatni element członkowski struktury. Może to być przydatne, jeśli rozmiar tablicy stałej różni się, gdy są używane w różnych sytuacjach. Deklaracja takiej struktury wygląda następująco:  
  
**Struktura** *identyfikator* **{** *zestawu z deklaracji* *typu* <em>nazwa tablicy</em> **\[]; };**  
  
Tablice bez określonego rozmiaru może znajdować się tylko jako ostatniej składowej struktury. Struktury zawierające deklaracje tablic bez określonego rozmiaru mogą być zagnieżdżane w innych struktur, tak długo, jak żadne dalsze składowe są deklarowane w dowolnej struktury otaczającej. Tablic z takimi strukturami nie są dozwolone. `sizeof` Operatora, po zastosowaniu do zmiennej tego typu lub sam typ, zakłada, 0, aby uzyskać rozmiar tablicy.  
  
Deklaracje struktur można również określić bez deklarator, gdy są oni członkami innej struktury lub Unii. Nazwy pól są promowane do otaczającej strukturze. Na przykład struktura pustego wygląda następująco:

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
  
Zobacz [składowe struktury i złożenia](../c-language/structure-and-union-members.md) uzyskać informacji na temat struktury odwołania.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)