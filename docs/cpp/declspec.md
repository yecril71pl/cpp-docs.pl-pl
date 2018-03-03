---
title: __declspec | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __declspec_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++]
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51a08092160ecb288decae343713e5a4f6e507b1
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="declspec"></a>__declspec

**Microsoft Specific**

Składnia rozszerzonych atrybutów do określenia klasy magazynowania informacji używa **__declspec** — słowo kluczowe, które określa, że mają być przechowywane z atrybutem klasy magazynu specyficzne dla firmy Microsoft wymienione poniżej wystąpienia danego typu. Przykładami innych modyfikatorów klasy magazynowania **statycznych** i **extern** słów kluczowych. Jednak te słowa kluczowe są częścią specyfikacji ANSI w językach C i C++ i jako takie nie są objęte składnią atrybutów rozszerzonych. Składnia atrybutu rozszerzonego upraszcza i standaryzuje rozszerzenia języków C i C++ specyficzne dla Microsoft.

## <a name="grammar"></a>Gramatyka

*Specyfikator Decl*:  
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (***rozszerzony decl — modyfikator seq***)** 

*rozszerzony decl — modyfikator seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony decl — modyfikator*<sub>opcjonalnych</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony decl — modyfikator* *rozszerzony decl — modyfikator seq*

*rozszerzony decl — modyfikator*:  
&nbsp;&nbsp;&nbsp;&nbsp;**Dopasuj (**  *#*  **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**Przydziel ("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**domeny aplikacji**  
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**przestarzałe**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**  
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**  
&nbsp;&nbsp;&nbsp;&nbsp;**naked**  
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**  
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**  
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**  
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**  
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**  
&nbsp;&nbsp;&nbsp;&nbsp;**proces**  
&nbsp;&nbsp;&nbsp;&nbsp;**Właściwość (** { **uzyskać =**_get_func_name_ &#124; **, umieść =**_put_func_name_ } **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**Ogranicz**  
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**  
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**  
&nbsp;&nbsp;&nbsp;&nbsp;**spectre(nomitigation)**  
&nbsp;&nbsp;&nbsp;&nbsp;**Wątek**  
&nbsp;&nbsp;&nbsp;&nbsp;**uuid("** *ComObjectGUID* **")**  

Spacja oddziela sekwencje modyfikatora deklaracji. Przykłady są zamieszczone w kolejnych sekcjach.

Atrybut rozszerzony gramatyki obsługuje te atrybuty klasy magazynu specyficzne dla firmy Microsoft: [Dopasuj](../cpp/align-cpp.md), [przydzielić](../cpp/allocate.md), [elementu appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [przestarzałe](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [procesu](../cpp/process.md), [ograniczyć](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [spectre](../cpp/spectre.md), i [wątku](../cpp/thread.md). Obsługuje ona również te atrybuty obiektu COM: [właściwości](../cpp/property-cpp.md) i [uuid](../cpp/uuid-cpp.md).

**Code_seg**, **dllexport**, **dllimport**, **naked**, **noalias**, **nothrow** , **właściwości**, **ograniczyć**, **selectany**, **wątku**, i **uuid**atrybuty klasy magazynu są tylko właściwości deklaracji obiektu lub funkcja, do której są stosowane. **Wątku** atrybut wpływa na dane i tylko obiekty. **Naked** i **spectre** tylko funkcje wpływają na atrybuty. **Dllimport** i **dllexport** atrybuty mają wpływ na funkcje, danych i obiektów. **Właściwości**, **selectany**, i **uuid** atrybuty wpływają na obiekty COM.

**__Declspec** słów kluczowych powinna zostać umieszczona na początku deklaracji proste. Kompilator ignoruje bez ostrzeżenia, w każdym **__declspec** słów kluczowych jest umieszczany po * lub & i przed identyfikatorem zmiennej w deklaracji.

A **__declspec** określony na początku deklaracji typu zdefiniowanego przez użytkownika atrybut ma zastosowanie do zmiennej typu. Na przykład:

```cpp
__declspec(dllimport) class X {} varX;
```

W takim przypadku atrybut ma zastosowanie do `varX`. A **__declspec** atrybut umieszczany po **klasy** lub **struktury** — słowo kluczowe dotyczy typ zdefiniowany przez użytkownika. Na przykład:

```cpp
class __declspec(dllimport) X {};
```

W takim przypadku atrybut ma zastosowanie do `X`.

Ogólne wytyczne dotyczące korzystania z **__declspec** atrybutu proste deklaracje wygląda następująco:

*decl-specifier-seq* *init-declarator-list*;

*Decl — specyfikator seq* powinien zawierać między innymi typu podstawowego (np. **int**, **float**, **typedef**, lub nazwy klasy), Klasa magazynu (np. **statycznych**, **extern**), lub **__declspec** rozszerzenia. *Init deklarator listy* powinien zawierać między innymi wskaźnika część deklaracji. Na przykład:

```cpp
__declspec(selectany) int * pi1 = 0;   //Recommended, selectany & int both part of decl-specifier
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator
```

Poniższy kod deklaruje zmienną całkowitoliczbową wątku lokalnego i inicjuje ją z wartością:

```cpp
// Example of the __declspec keyword
__declspec( thread ) int tls_i = 1;
```

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)  
[Rozszerzone atrybuty klasy magazynu języka C](../c-language/c-extended-storage-class-attributes.md)  
