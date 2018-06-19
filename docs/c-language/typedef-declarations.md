---
title: Deklaracje TypeDef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, typedef
- typedef declarations
- types [C], declarations
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 192f7ab037362219261852cfdb0a5eac53e5df9f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391655"
---
# <a name="typedef-declarations"></a>Deklaracje typedef
Deklaracji typedef jest deklaracją z typedef jako klasa magazynu. Deklarator staje się nowego typu. Deklaracje typedef można użyć do utworzenia krótszy lub bardziej zrozumiałej nazwy dla typów zdefiniowanych przez C lub dla typów, które zostały zadeklarowane. Nazwy zdefiniowane przez typedef pozwalają na hermetyzację szczegółów implementacji, które mogą się zmieniać.  
  
 Deklaracji typedef jest interpretowana w taki sam sposób jak zmienna lub deklaracji funkcji, ale identyfikator, zamiast zakładając, że typ określony w deklaracji, staje się synonim dla typu.  
  
## <a name="syntax"></a>Składnia  
 `declaration`:  
 *Specyfikatory deklaracji w init listy deklarator* opt **;**  
  
 *Specyfikatory deklaracji*:  
 *Specyfikatory deklaracji Specyfikator klasy magazynu* opcjonalnych  
  
 *Specyfikatory deklaracji specyfikatora typu* opcjonalnych  
  
 *Specyfikatory deklaracji kwalifikator typu* opcjonalnych  
  
 *storage-class-specifier*:  
 `typedef`  
  
 *Specyfikator typu*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **Podpisany**  
  
 **Bez znaku**  
  
 *struct-or-union-specifier*  
  
 *enum-specifier*  
  
 *Nazwa typu TypeDef*  
  
 *Nazwa typu TypeDef*:  
 *Identyfikator*  
  
 Należy pamiętać, że deklaracji typedef nie tworzy typy. Tworzy synonimy dla istniejących typów lub nazwy dla typów, które można określić w inny sposób. Gdy nazwa typu typedef jest używane jako Specyfikator typu, można łączyć z niektórych specyfikatorze typu, ale nie. Modyfikatory dopuszczalne obejmują **const** i `volatile`.  
  
 Nazwy elementów TypeDef udostępniać przestrzeń nazw zwykłej identyfikatory (zobacz [przestrzeniach nazw](../c-language/name-spaces.md) Aby uzyskać więcej informacji). Program może mieć więc nazwę typedef i identyfikator o zakresie lokalnym o tej samej nazwie. Na przykład:  
  
```  
typedef char FlagType;  
  
int main()  
{  
}  
  
int myproc( int )  
{  
    int FlagType;  
}  
```  
  
 Podczas deklarowania identyfikatora o zakresie lokalnym o tej samej nazwie co element typedef lub podczas deklarowania elementu struktury lub unii w tym samym zakresie lub w zakresie wewnętrznym, należy określić specyfikator typu. W tym przykładzie przedstawiono tego ograniczenia:  
  
```  
typedef char FlagType;  
const FlagType x;  
```  
  
 Aby ponownie użyć nazwy `FlagType` dla identyfikatora, elementu struktury lub unii musi zostać dostarczony typ:  
  
```  
const int FlagType;  /* Type specifier required */  
```  
  
 Nie wystarczy powiedzieć  
  
```  
const FlagType;      /* Incomplete specification */  
```  
  
 ponieważ `FlagType` uważa się za część typu, a nie identyfikatora, który jest ponownie deklarowany. Taką deklarację uważa się za niedozwoloną, tak jak  
  
```  
int;  /* Illegal declaration */  
```  
  
 Można zadeklarować dowolny typ z typedef, w tym wskaźnik, funkcję i typy tablic. Można zadeklarować nazwę typedef wskaźnika na strukturę lub unię przed zdefiniowaniem struktury lub unii, tak długo jak definicja ma taką samą widoczność jak deklaracja.  
  
 Nazwy elementów TypeDef można poprawić czytelność kodu. Wszystkie trzy następujące deklaracje `signal` Określ dokładnie tego samego typu, najpierw bez wprowadzania Użyj dowolnej nazwy elementów typedef.  
  
```  
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */  
  
void ( *signal( int, void (*) (int)) ) ( int );  
fv *signal( int, fv * );   /* Uses typedef type */  
pfv signal( int, pfv );    /* Uses typedef type */  
```  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady przedstawiają deklaracje typedef:  
  
```  
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */  
```  
  
 Należy pamiętać, że `WHOLE` można teraz używać w deklaracji zmiennej takich jak `WHOLE i;` lub `const WHOLE i;`. Jednak deklaracji `long WHOLE i;` jest niedozwolone.  
  
```  
typedef struct club   
{  
    char name[30];  
    int size, year;  
} GROUP;  
```  
  
 Ta instrukcja deklaruje `GROUP` jako typ struktury z trzech elementów członkowskich. Od znacznika struktury `club`, również jest określony, nazwa typu typedef (`GROUP`) lub tagu struktury można używać w deklaracjach. Należy użyć struct, słowo kluczowe z tagu, a nazwa typu typedef nie można używać struct, słowo kluczowe.  
  
```  
typedef GROUP *PG; /* Uses the previous typedef name   
                      to declare a pointer            */  
```  
  
 Typ `PG` jest zadeklarowany jako wskaźnik do `GROUP` typu, który z kolei jest zdefiniowana jako typ struktury.  
  
```  
typedef void DRAWF( int, int );  
```  
  
 W poniższym przykładzie przedstawiono typ `DRAWF` dla funkcji zwracających wartości i podjęcie dwa argumenty int. Oznacza to, na przykład, że deklaracja  
  
```  
DRAWF box;   
```  
  
 jest odpowiednikiem deklaracji  
  
```  
void box( int, int );  
```  
  
## <a name="see-also"></a>Zobacz też  


