---
title: __declspec | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++]
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f413c56b665a1878fb1e948b975ab8e4cbc0daf4
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163591"
---
# <a name="declspec"></a>__declspec

**Microsoft Specific**

Składnia atrybutów rozszerzonych służących do określania informacji klasy magazynowania wykorzystuje **__declspec** słowo kluczowe, które określa, że wystąpienie danego typu jest mają być przechowywane z atrybutem klasy magazynowania specyficzne dla firmy Microsoft wymienione poniżej. Przykłady innych modyfikatorów klasy magazynowania **statyczne** i **extern** słów kluczowych. Jednak te słowa kluczowe są częścią specyfikacji ANSI w językach C i C++ i jako takie nie są objęte składnią atrybutów rozszerzonych. Składnia atrybutu rozszerzonego upraszcza i standaryzuje rozszerzenia języków C i C++ specyficzne dla Microsoft.

## <a name="grammar"></a>Gramatyka

*Decl-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (***extended-decl modyfikator seq***)** 

*rozszerzony decl modyfikator seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony decl modyfikator*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony decl modyfikator* *extended-decl modyfikator seq*

*rozszerzony decl modyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Wyrównaj (** *#* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przydziel ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**domeny aplikacji**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**przestarzałe**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**DllImport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"naked"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Proces**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**właściwości (** { **uzyskać =**_get_func_name_ &#124; **, umieść =**_put_func_name_ } **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**ograniczenia**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**spectre(nomitigation)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Wątek**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Identyfikator UUID ("** *ComObjectGUID* **")**

Spacja oddziela sekwencje modyfikatora deklaracji. Przykłady są zamieszczone w kolejnych sekcjach.

Gramatyka atrybutów rozszerzonych obsługuje te atrybuty klasy magazynu specyficzne dla firmy Microsoft: [wyrównać](../cpp/align-cpp.md), [przydzielić](../cpp/allocate.md), [appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [przestarzałe](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), ["naked"](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [procesu](../cpp/process.md), [ograniczyć](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [krokami zaradczymi dla luki](../cpp/spectre.md), i [wątku](../cpp/thread.md). Obsługuje również te atrybuty obiektu COM: [właściwość](../cpp/property-cpp.md) i [uuid](../cpp/uuid-cpp.md).

**Code_seg**, **dllexport**, **dllimport**, **"naked"**, **noalias**, **nothrow** , **właściwość**, **ograniczyć**, **selectany**, **wątku**, i **uuid**atrybuty klasy magazynu są właściwości tylko dla deklaracji obiektu lub funkcji, do której są stosowane. **Wątku** atrybut ma wpływ na dane i obiekty tylko. **"Naked"** i **krokami zaradczymi dla luki** tylko funkcje mają wpływ na atrybuty. **Dllimport** i **dllexport** atrybuty mają wpływ na funkcje, dane i obiekty. **Właściwość**, **selectany**, i **uuid** atrybuty mają wpływ na obiekty COM.

W celu zgodności z poprzednimi wersjami **_declspec** jest synonimem dla **__declspec** chyba że — opcja kompilatora [/Za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

**__Declspec** słów kluczowych, powinny być umieszczone na początku zwykłej deklaracji. Kompilator ignoruje, bez ostrzeżenia, wszelkie **__declspec** słowa kluczowe umieszczone po * lub & i przed identyfikatorem zmiennej w deklaracji.

A **__declspec** atrybutu wskazanego w początku deklaracji typu zdefiniowanego przez użytkownika stosuje się do zmiennej tego typu. Na przykład:

```cpp
__declspec(dllimport) class X {} varX;
```

W tym przypadku atrybut dotyczy `varX`. A **__declspec** atrybut umieszczone po **klasy** lub **struktury** słowa kluczowego ma zastosowanie do typu zdefiniowanego przez użytkownika. Na przykład:

```cpp
class __declspec(dllimport) X {};
```

W tym przypadku atrybut dotyczy `X`.

Ogólne wytyczne dotyczące korzystania **__declspec** atrybutu dla prostych deklaracji są następujące:

*decl-specifier-seq* *init-declarator-list*;

*Decl-specifier-seq* powinien zawierać, między innymi, typ podstawowy (np. **int**, **float**, **typedef**, lub nazwy klasy), Klasa magazynu (np. **statyczne**, **extern**), lub **__declspec** rozszerzenia. *Init-declarator-list* powinien zawierać, między innymi, część wskaźnika deklaracji. Na przykład:

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Rozszerzone atrybuty klasy magazynu języka C](../c-language/c-extended-storage-class-attributes.md)