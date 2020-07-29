---
title: Rozszerzone atrybuty klasy magazynu języka C
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
ms.openlocfilehash: 5e1fe80f3bc1f581c6ea05c54409b1e76eacfce7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87190224"
---
# <a name="c-extended-storage-class-attributes"></a>Rozszerzone atrybuty klasy magazynu języka C

**Specyficzne dla firmy Microsoft**

Więcej informacji na ten temat można znaleźć w obszarze [__declspec (odwołanie w C++)](../cpp/declspec.md).

Składnia atrybutu rozszerzonego upraszcza i standaryzacj rozszerzenia specyficzne dla firmy Microsoft w języku C. Atrybuty klasy magazynowania, które używają składni atrybutów rozszerzonych, obejmują Thread, owies, dllimport i dllexport.

Składnia atrybutu rozszerzonego określająca informacje klasy magazynu używa słowa kluczowego __declspec, które określa, że wystąpienie danego typu ma być przechowywane z atrybutem klasy magazynowania specyficznym dla firmy Microsoft (wątek, niezależny, dllimport lub dllexport). Przykłady innych modyfikatorów klasy magazynu obejmują słowa kluczowe static i extern. Jednak te słowa kluczowe są częścią standardu ANSI C i nie są objęte składnią atrybutów rozszerzonych.

## <a name="syntax"></a>Składnia

*specyfikator klasy magazynu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *rozszerzony-decl-modyfikator-SEQ* **)**  / \* Specyficzne dla firmy Microsoft\*/

*Extended-decl-modyfikator-SEQ*: &nbsp; &nbsp; &nbsp; &nbsp; / \* specyficzny dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony-decl-modyfikator*<sub>wyboru</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modyfikator-SEQ* *Extended-decl-modyfikator*

*Extended-decl-modyfikator*: &nbsp; &nbsp; &nbsp; &nbsp; / \* specyficzny dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`thread`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`naked`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllimport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllexport`**

Biały znak oddziela Modyfikatory deklaracji. Należy zauważyć, że *rozszerzony-decl-modyfikator-SEQ* może być pusty; w takim przypadku __declspec nie ma żadnego wpływu.

Atrybuty klasy magazynu "threaded, dllimport" i "dllexport" są właściwością tylko deklaracji danych lub funkcji, do których są stosowane; nie definiują one atrybutów typu samej funkcji. Atrybut Thread ma wpływ tylko na dane. Atrybut owies ma wpływ tylko na funkcje. Atrybuty dllimport i dllexport mają wpływ na funkcje i dane.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)
