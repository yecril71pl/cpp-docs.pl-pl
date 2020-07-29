---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: 945202beca6c5deb525bd19886b947331f6f3ac3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228950"
---
# `__declspec`

**Specyficzne dla firmy Microsoft**

Składnia atrybutu rozszerzonego określająca informacje klasy magazynu używa **`__declspec`** słowa kluczowego, które określa, że wystąpienie danego typu ma być przechowywane z atrybutem klasy magazynowania specyficznym dla firmy Microsoft wymienionym poniżej. Przykłady innych modyfikatorów klasy magazynu obejmują **`static`** **`extern`** słowa kluczowe i. Jednak te słowa kluczowe są częścią specyfikacji ANSI w językach C i C++ i jako takie nie są objęte składnią atrybutów rozszerzonych. Składnia atrybutu rozszerzonego upraszcza i standaryzuje rozszerzenia języków C i C++ specyficzne dla Microsoft.

## <a name="grammar"></a>Gramatyka

*decl — specyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__declspec (`**  *Extended-decl-modyfikator-SEQ*  **`)`**

*Extended-decl-modyfikator-SEQ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony-decl-modyfikator*<sub>wyboru</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modyfikator* *Extended-decl-modyfikator-SEQ*

*Extended-decl-modyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`align(`** *#* **`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`allocate("`***segname***`")`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`allocator`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`appdomain`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`code_seg("`***segname***`")`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`deprecated`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllimport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllexport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`jitintrinsic`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`naked`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noalias`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noinline`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noreturn`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`nothrow`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`novtable`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`process`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`property(`**{ **`get=`** _get_func_name_ &#124; **`,put=`** _put_func_name_ }**`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`restrict`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`safebuffers`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`selectany`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`spectre(nomitigation)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`thread`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`uuid("`***ComObjectGUID***`")`**

Spacja oddziela sekwencje modyfikatora deklaracji. Przykłady są zamieszczone w kolejnych sekcjach.

Rozszerzony Gramatyka atrybutów obsługuje te atrybuty klasy magazynu specyficznych dla firmy Microsoft:,,,,,,,,,, [`align`](../cpp/align-cpp.md) [`allocate`](../cpp/allocate.md) [`allocator`](../cpp/allocator.md) [`appdomain`](../cpp/appdomain.md) [`code_seg`](../cpp/code-seg-declspec.md) [`deprecated`](../cpp/deprecated-cpp.md) [`dllexport`](../cpp/dllexport-dllimport.md) [`dllimport`](../cpp/dllexport-dllimport.md) [`jitintrinsic`](../cpp/jitintrinsic.md) [`naked`](../cpp/naked-cpp.md) [`noalias`](../cpp/noalias.md) , [`noinline`](../cpp/noinline.md) ,, [`noreturn`](../cpp/noreturn.md) [`nothrow`](../cpp/nothrow-cpp.md) , [`novtable`](../cpp/novtable.md) , [`process`](../cpp/process.md) , [`restrict`](../cpp/restrict.md) , [`safebuffers`](../cpp/safebuffers.md) ,, [`selectany`](../cpp/selectany.md) [`spectre`](../cpp/spectre.md) , i [`thread`](../cpp/thread.md) . Obsługuje również te atrybuty obiektu COM: [`property`](../cpp/property-cpp.md) i [`uuid`](../cpp/uuid-cpp.md) .

Atrybuty klasy,,,,,,,,, **`code_seg`** **`dllexport`** **`dllimport`** **`naked`** **`noalias`** **`nothrow`** **`property`** **`restrict`** **`selectany`** **`thread`** i **`uuid`** są właściwości tylko deklaracji obiektu lub funkcji, do których są stosowane. Ten **`thread`** atrybut ma wpływ tylko na dane i obiekty. **`naked`** Atrybuty i **`spectre`** mają wpływ tylko na funkcje. **`dllimport`** Atrybuty i **`dllexport`** mają wpływ na funkcje, dane i obiekty. **`property`** Atrybuty, **`selectany`** i **uu'id** mają wpływ na obiekty com.

W celu zapewnienia zgodności z poprzednimi wersjami, **`_declspec`** jest synonimem, **`__declspec`** Jeśli opcja kompilatora [/za \( wyłączone rozszerzenia językowe](../build/reference/za-ze-disable-language-extensions.md) nie została określona.

**`__declspec`** Słowa kluczowe należy umieścić na początku prostej deklaracji. Kompilator ignoruje, bez ostrzeżenia, wszystkie **`__declspec`** słowa kluczowe umieszczone po * lub & i przed identyfikatorem zmiennej w deklaracji.

**`__declspec`** Atrybut określony na początku deklaracji typu zdefiniowanego przez użytkownika ma zastosowanie do zmiennej tego typu. Na przykład:

```cpp
__declspec(dllimport) class X {} varX;
```

W takim przypadku atrybut ma zastosowanie do `varX` . **`__declspec`** Atrybut umieszczony po **`class`** **`struct`** słowie kluczowym or ma zastosowanie do typu zdefiniowanego przez użytkownika. Na przykład:

```cpp
class __declspec(dllimport) X {};
```

W takim przypadku atrybut ma zastosowanie do `X` .

Ogólne wytyczne dotyczące korzystania z **`__declspec`** atrybutu dla prostych deklaracji są następujące:

*decl-specyfikator-SEQ* *init-deklarator-list*;

Element *decl-specyfikator-SEQ* powinien zawierać, między innymi, typ podstawowy (np.,, **`int`** **`float`** **`typedef`** lub nazwę klasy), klasę magazynu (np. **`static`** **`extern`** ) lub **`__declspec`** rozszerzenie. Element *init-deklarator-list* powinien zawierać, między innymi, część wskaźnika deklaracji. Na przykład:

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

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Rozszerzone atrybuty klasy magazynu języka C](../c-language/c-extended-storage-class-attributes.md)
