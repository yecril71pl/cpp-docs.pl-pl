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
ms.openlocfilehash: e7d305b2bc74455abd6fdbcfb29ed7ef4103bf19
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="structure-declarations"></a>Deklaracje struktur
"Deklaracja struktury" nazwy typu i określa sekwencję wartości zmiennych (nazywany "Członkowie" lub "pola" konstrukcji), które mogą mieć różnych typów. Opcjonalny identyfikator o nazwie "tag", nadaje nazwę typu struktury i mogą być używane w kolejnych odwołań do typ struktury. Zmienna typu Struktura zawiera całą sekwencję wynika z tego typu. Struktury w języku C są podobne do typów znana jako "rekordy" w innych językach.  
  
## <a name="syntax"></a>Składnia  
 *struct-or-union-specifier*:  
 *Identyfikator struktury lub Unii* opt **{** *struktury deklaracji listy* **}**  
  
 *Identyfikator struktury lub związku*  
  
 *struct-or-union*:  
 **struct**  
  
 **Unii**  
  
 *struct-declaration-list*:  
 *struct-declaration*  
  
 *Deklaracja struktury deklaracjach — struktura*  
  
 Struktura zawartości jest zdefiniowany  
  
 *struct-declaration*:  
 *Specyfikator kwalifikator listy w strukturze listy deklarator***;**  
  
 *specifier-qualifier-list*:  
 *Specyfikator typu w specyfikatorze listy kwalifikator* opcjonalnych  
  
 *Kwalifikator typu w specyfikatorze listy kwalifikator* opcjonalnych  
  
 *struct-declarator-list*:  
 *deklarator — struktura*  
  
 *Struktura deklarator listy***,***deklarator — struktura*   
  
 *struct-declarator*:  
 `declarator`  
  
 Deklaracja typu struktury nie zarezerwowane miejsce dla struktury. Jest tylko szablon dla nowszej deklaracje zmiennych struktury.  
  
 A uprzednio zdefiniowany *identyfikator* (tagów) może służyć do odwołuje się do typu struktury zdefiniowany w innym miejscu. W takim przypadku *struktury deklaracji listy* nie może powtarzać się tak długo, jak definicji jest widoczny. Deklaracje wskaźników do struktur i definicje typów dla typów struktury można zastosować tag struktury, przed zdefiniowaniem typ struktury. Jednak definicji struktury musi wystąpić przed jakimkolwiek użyciem rzeczywisty rozmiar pól. To jest niekompletna definicja typu i tag typu. Definicja ta zostanie ukończona definicją typu musi występować później w tym samym zakresie.  
  
 *Struktury deklaracji listy* Określa typy i nazwy elementów członkowskich struktury. A *struktury deklaracji listy* argument zawiera co najmniej jednej zmiennej lub pola bitowego deklaracji.  
  
 Każdej zmiennej zadeklarowanej w *struktury deklaracji listy* jest zdefiniowany jako element członkowski typu struktury. Deklaracje zmiennej w ramach *struktury deklaracji listy* mieć tego samego formularza jako innych deklaracji zmiennych, które zostały omówione w tej sekcji, z wyjątkiem tego, czy deklaracje nie może zawierać specyfikatory klasy magazynowania lub inicjatorów. Elementy członkowskie struktury może mieć żadnych zmiennych typów, z wyjątkiem typu `void`, niekompletnego typu lub typu funkcji.  
  
 Element członkowski nie można zadeklarować typu struktury, w których występuje. Jednak element członkowski mogą być deklarowane jako wskaźnik do typu struktury, w której występuje tak długo, jak typ struktury ma tag. Dzięki temu można utworzyć połączonej listy struktur.  
  
 Struktury postępuj zgodnie z tego samego zakresu jako innych identyfikatorów. Struktura identyfikatory muszą być różne od innych strukturę, Unii i tagi wyliczania z taką samą widoczność.  
  
 Każdy *deklaracji struktury* w *struktury deklaracji listy* muszą być unikatowe w obrębie listy. Jednakże identyfikatora nazwy w *struktury deklaracji listy* nie muszą się różnić od zwykłej nazwy zmiennych lub identyfikatorów list deklaracji struktury.  
  
 Zagnieżdżone struktury są dostępne również tak, jakby zostały zgłoszone na poziomie zakresu pliku. Przykładowo podana tej deklaracji:  
  
```  
struct a  
{  
    int x;  
    struct b  
    {  
      int y;  
    } var2;  
} var1;  
```  
  
 Deklaracje te są prawnych:  
  
```  
struct a var3;  
struct b var4;  
```  
  
## <a name="examples"></a>Przykłady  
 Tych przykładach deklaracje struktur:  
  
```  
struct employee   /* Defines a structure variable named temp */  
{  
    char name[20];  
    int id;  
    long class;  
} temp;  
```  
  
 `employee` Struktury ma trzy elementy członkowskie: `name`, `id`, i `class`. `name` Element członkowski jest tablicą 20 element i `id` i `class` są proste elementy członkowskie o `int` i **długi** wpisz odpowiednio. Identyfikator `employee` jest identyfikatorem struktury.  
  
```  
struct employee student, faculty, staff;  
```  
  
 W tym przykładzie definiuje trzy zmienne struktury: `student`, `faculty`, i `staff`. Każda struktura ma tę samą listę trzech elementów członkowskich. Elementy członkowskie są deklarowane jako typ struktury `employee`zdefiniowanej w poprzednim przykładzie.  
  
```  
struct           /* Defines an anonymous struct and a */  
{                /* structure variable named complex  */  
    float x, y;  
} complex;  
```  
  
 `complex` Struktury ma dwa elementy członkowskie z **float** typu `x` i `y`. Typ struktury nie ma tagu i dlatego jest bez nazwy lub anonimowe.  
  
```  
struct sample   /* Defines a structure named x */  
{  
    char c;  
    float *pf;  
    struct sample *next;  
} x;  
```  
  
 Pierwsze dwa elementy członkowskie struktury są `char` zmienną i wskaźnika do **float** wartość. Trzeci członek `next`, jest zadeklarowany jako wskaźnik do zdefiniowanych struktury (`sample`).  
  
 Struktury anonimowe mogą być przydatne, gdy tag o nazwie nie jest wymagana. Jest to sytuacji, gdy wszystkie wystąpienia struktury definiuje jedną deklarację. Na przykład:  
  
```  
struct  
{  
    int x;  
    int y;  
} mystruct;  
```  
  
 Struktury osadzone często są anonimowe.  
  
```  
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
  
 Kompilator umożliwia bez określonego rozmiaru lub zerowy rozmiar tablicy jako ostatni element członkowski struktury. Może to być przydatne, jeśli rozmiar tablicy stałej różni się w różnych sytuacjach. Deklaracja taka struktura wygląda następująco:  
  
 `struct` *Identyfikator *** {** *zestawu z deklaracji* *typu tablicy — [nazwa ***];};**  
  
 Tablic bez określonego rozmiaru może występować tylko jako ostatni element członkowski struktury. Struktury zawierające deklaracje bez określonego rozmiaru tablicy mogą być zagnieżdżane w innych konstrukcji tak długo, jak długo ma więcej elementów członkowskich są zadeklarowane w dowolnej struktury otaczającej. Tablice takie struktury są niedozwolone. `sizeof` Operatora, gdy jest stosowany do zmiennej tego typu lub sam typ zakłada 0 dla rozmiaru tablicy.  
  
 Deklaracje struktur można również określić bez deklaratorze, gdy są oni członkami innego struktury lub związku. Nazwy pól są awansowane w otaczającej strukturę. Na przykład typ struktury wygląda następująco:  
  
```  
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
  
 Zobacz [struktury i elementów członkowskich Unii](../c-language/structure-and-union-members.md) uzyskać informacji o odwołaniach struktury.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)