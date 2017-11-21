---
title: __declspec | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __declspec_cpp
dev_langs: C++
helpviewer_keywords: __declspec keyword [C++]
ms.assetid: 832db681-e8e1-41ca-b78c-cd9d265cdb87
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 294f6060ed163906ba4e9eeaca034ab7cbfc1205
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="declspec"></a>__declspec
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Składnia rozszerzonych atrybutów do określenia klasy magazynowania informacji używa `__declspec` — słowo kluczowe, które określa, że mają być przechowywane z atrybutem klasy magazynu specyficzne dla firmy Microsoft wymienione poniżej wystąpienia danego typu. Przykładami innych modyfikatorów klasy magazynowania `static` i `extern` słów kluczowych. Jednak te słowa kluczowe są częścią specyfikacji ANSI w językach C i C++ i jako takie nie są objęte składnią atrybutów rozszerzonych. Składnia atrybutu rozszerzonego upraszcza i standaryzuje rozszerzenia języków C i C++ specyficzne dla Microsoft.  
  
## <a name="grammar"></a>Gramatyka  
 *Specyfikator Decl*:  
 `__declspec (`  *rozszerzony decl — modyfikator seq*  `)`  
  
 *rozszerzony decl — modyfikator seq*:  
 *rozszerzony decl — modyfikator*opcjonalnych  
  
 *rozszerzony decl — modyfikator rozszerzony decl — modyfikator seq*  
  
 *rozszerzony decl — modyfikator*:  
 `align(` *#* `)`  
  
 `allocate("`*segname*`")`  
  
 `appdomain`  
  
 `code_seg("`*segname*`")`  
  
 `deprecated`  
  
 `dllimport`  
  
 `dllexport`  
  
 `jitintrinsic`  
  
 `naked`  
  
 `noalias`  
  
 `noinline`  
  
 `noreturn`  
  
 `nothrow`  
  
 `novtable`  
  
 `process`  
  
 `property(`{`get=`*get_func_name*&#124;`,put=` *put_func_name*}`)`  
  
 `restrict`  
  
 `safebuffers`  
  
 `selectany`  
  
 `thread`  
  
 `uuid("`*ComObjectGUID*`")`  
  
 Spacja oddziela sekwencje modyfikatora deklaracji. Przykłady są zamieszczone w kolejnych sekcjach.  
  
 Atrybut rozszerzony gramatyki obsługuje te atrybuty klasy magazynu specyficzne dla firmy Microsoft: [Dopasuj](../cpp/align-cpp.md), [przydzielić](../cpp/allocate.md), [elementu appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [przestarzałe](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [procesu](../cpp/process.md), [ograniczyć](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), i [wątku](../cpp/thread.md). Obsługuje ona również te atrybuty obiektu COM: [właściwości](../cpp/property-cpp.md) i [uuid](../cpp/uuid-cpp.md).  
  
 `code_seg`, `dllexport`, `dllimport`, `naked`, `noalias`, `nothrow`, `property`, `restrict`, `selectany`, `thread`, I `uuid` atrybuty klasy magazynu tylko deklaracji obiektu lub funkcja, do której są stosowane. `thread` Atrybut wpływa na dane i tylko obiekty. `naked` Atrybut dotyczy tylko funkcji. `dllimport` i `dllexport` atrybuty mają wpływ na funkcje, danych i obiektów. `property`, `selectany`, I `uuid` atrybuty wpływają na obiekty COM.  
  
 `__declspec` Słów kluczowych powinna zostać umieszczona na początku deklaracji proste. Kompilator ignoruje bez ostrzeżenia, w każdym `__declspec` słów kluczowych jest umieszczany po * lub & i przed identyfikatorem zmiennej w deklaracji.  
  
 A `__declspec` określony na początku deklaracji typu zdefiniowanego przez użytkownika atrybut ma zastosowanie do zmiennej typu. Na przykład:  
  
```  
__declspec(dllimport) class X {} varX;  
```  
  
 W takim przypadku atrybut ma zastosowanie do `varX`. A `__declspec` atrybut umieszczany po `class` lub `struct` — słowo kluczowe dotyczy typ zdefiniowany przez użytkownika. Na przykład:  
  
```  
class __declspec(dllimport) X {};  
```  
  
 W takim przypadku atrybut ma zastosowanie do `X`.  
  
 Ogólne wytyczne dotyczące korzystania z `__declspec` atrybutu proste deklaracje wygląda następująco:  
  
```  
  
decl-specifier-seq  
declarator-list;  
```  
  
 *Decl — specyfikator seq* powinien zawierać między innymi typu podstawowego (np. `int`, `float`, `typedef`, lub nazwy klasy), klasę magazynu (np. `static`, `extern`), lub `__declspec`rozszerzenia. *Init deklarator listy* powinien zawierać między innymi wskaźnika część deklaracji. Na przykład:  
  
```  
__declspec(selectany) int * pi1 = 0;   //OK, selectany & int both part of decl-specifier  
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier  
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator  
```  
  
 Poniższy kod deklaruje zmienną całkowitoliczbową wątku lokalnego i inicjuje ją z wartością:  
  
```  
// Example of the __declspec keyword  
__declspec( thread ) int tls_i = 1;  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [C rozszerzone atrybuty klasy magazynu](../c-language/c-extended-storage-class-attributes.md)