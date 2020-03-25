---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: e0c99ea9379aa6e29096250e8bd36ce3d4f183e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180228"
---
# <a name="__declspec"></a>__declspec

**Specyficzne dla firmy Microsoft**

Składnia atrybutu rozszerzonego określająca informacje klasy magazynu używa słowa kluczowego **__declspec** , które określa, że wystąpienie danego typu ma być przechowywane z atrybutem klasy magazynowania specyficznym dla firmy Microsoft wymienionym poniżej. Przykłady innych modyfikatorów klasy magazynu obejmują słowa kluczowe **static** i **extern** . Jednak te słowa kluczowe są częścią specyfikacji ANSI w językach C i C++ i jako takie nie są objęte składnią atrybutów rozszerzonych. Składnia atrybutu rozszerzonego upraszcza i standaryzuje rozszerzenia języków C i C++ specyficzne dla Microsoft.

## <a name="grammar"></a>Gramatyka

*decl — specyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *rozszerzony-decl-modyfikator-SEQ* **)**

*Extended-decl-modyfikator-SEQ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony-decl-modyfikator*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony-decl-modyfikator* *rozszerzony-decl-modyfikator-SEQ*

*Extended-decl-modyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**align (** *#* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**przydzielenia ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;**alokatora** &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**AppDomain**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**przestarzałe**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**NoLine**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**notablicę**<br/>
**proces** &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Właściwość (** { **Get =** _get_func_name_ &#124; **, Put =** _put_func_name_ } **)**<br/>
&nbsp;&nbsp;&nbsp;**ograniczenia** &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Spectre (nozaradcze)**<br/>
&nbsp;&nbsp;&nbsp;**wątku** &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**UUID ("** *ComObjectGUID* **")**

Spacja oddziela sekwencje modyfikatora deklaracji. Przykłady są zamieszczone w kolejnych sekcjach.

Rozszerzenie gramatyki atrybutów rozszerzonych obsługuje te atrybuty klasy magazynu specyficznych dla firmy Microsoft: [Wyrównaj](../cpp/align-cpp.md), [Przydziel](../cpp/allocate.md), [Alokator](../cpp/allocator.md), [AppDomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [przestarzałe](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [noaliasing](../cpp/noalias.md), [NoLine](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [notablicę](../cpp/novtable.md) [,](../cpp/naked-cpp.md) [Process](../cpp/process.md), [ograniczanie](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [ Spectre](../cpp/spectre.md)i [wątek](../cpp/thread.md). Obsługuje również te atrybuty obiektu COM: [Właściwość](../cpp/property-cpp.md) i [UUID](../cpp/uuid-cpp.md).

Atrybuty klasy magazynu **code_seg**, **dllexport**, **naked** **dllimport**, **unaliasing**, **nothrow**, **Property**, **ograniczenia**, **selectany**, **Thread**i **UUID** są właściwościami tylko deklaracji obiektu lub funkcji, do których są stosowane. Atrybut **Thread** ma wpływ tylko na dane i obiekty. Atrybuty **owies** i **Spectre** mają wpływ tylko na funkcje. Atrybuty **dllimport** i **dllexport** mają wpływ na funkcje, dane i obiekty. Atrybuty **Property**, **selectany**i **UUID** wpływają na obiekty com.

W celu zapewnienia zgodności z poprzednimi wersjami **_declspec** jest synonimem dla **__declspec** , chyba że opcja kompilatora [/za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) .

Słowa kluczowe **__declspec** należy umieścić na początku prostej deklaracji. Kompilator ignoruje, bez ostrzeżenia, wszelkie **__declspec** słowa kluczowe umieszczone po znaku * lub & i przed identyfikatorem zmiennej w deklaracji.

Atrybut **__declspec** określony na początku deklaracji typu zdefiniowanego przez użytkownika ma zastosowanie do zmiennej tego typu. Na przykład:

```cpp
__declspec(dllimport) class X {} varX;
```

W takim przypadku atrybut ma zastosowanie do `varX`. Atrybut **__declspec** umieszczony po słowie kluczowym **klasy** lub **struktury** ma zastosowanie do typu zdefiniowanego przez użytkownika. Na przykład:

```cpp
class __declspec(dllimport) X {};
```

W takim przypadku atrybut ma zastosowanie do `X`.

Ogólne wytyczne dotyczące korzystania z atrybutu **__declspec** dla prostych deklaracji są następujące:

*decl-specyfikator-SEQ* *init-deklarator-list*;

Element *decl-specyfikator-SEQ* powinien zawierać, między innymi, typ podstawowy (np. **int**, **float**, **typedef**lub nazwa klasy), klasę magazynu (np. **static**, **extern**) lub rozszerzenie **__declspec** . Element *init-deklarator-list* powinien zawierać, między innymi, część wskaźnika deklaracji. Na przykład:

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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Rozszerzone atrybuty klasy magazynu języka C](../c-language/c-extended-storage-class-attributes.md)
