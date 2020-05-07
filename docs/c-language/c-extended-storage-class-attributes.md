---
title: Rozszerzone atrybuty klasy magazynu języka C
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
ms.openlocfilehash: c2e372ebe93b9240ac6f489e8b1aefc1fbbded80
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857154"
---
# <a name="c-extended-storage-class-attributes"></a>Rozszerzone atrybuty klasy magazynu języka C

**Specyficzne dla firmy Microsoft**

Więcej informacji na ten temat można znaleźć w obszarze [__declspec (odwołanie w C++)](../cpp/declspec.md).

Składnia atrybutu rozszerzonego upraszcza i standaryzacj rozszerzenia specyficzne dla firmy Microsoft w języku C. Atrybuty klasy magazynowania, które używają składni atrybutów rozszerzonych, obejmują Thread, owies, dllimport i dllexport.

Składnia atrybutu rozszerzonego określająca informacje klasy magazynu używa słowa kluczowego __declspec, które określa, że wystąpienie danego typu ma być przechowywane z atrybutem klasy magazynowania specyficznym dla firmy Microsoft (wątek, niezależny, dllimport lub dllexport). Przykłady innych modyfikatorów klasy magazynu obejmują słowa kluczowe static i extern. Jednak te słowa kluczowe są częścią standardu ANSI C i nie są objęte składnią atrybutów rozszerzonych.

## <a name="syntax"></a>Składnia

*specyfikator klasy magazynu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *rozszerzony-decl-modyfikator-SEQ* **)**  / \* specyficzny dla firmy Microsoft\*/

*Extended-decl-modyfikator-SEQ*:&nbsp; &nbsp; &nbsp; &nbsp; / \* specyficzny dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony-decl-modyfikator*<sub>wyboru</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modyfikator-SEQ* *Extended-decl-modyfikator*

*Extended-decl-modyfikator*:&nbsp; &nbsp; &nbsp; &nbsp; / \* specyficzny dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nici**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**okiem**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

Biały znak oddziela Modyfikatory deklaracji. Należy zauważyć, że *rozszerzony-decl-modyfikator-SEQ* może być pusty; w takim przypadku __declspec nie ma żadnego wpływu.

Atrybuty klasy magazynu "threaded, dllimport" i "dllexport" są właściwością tylko deklaracji danych lub funkcji, do których są stosowane; nie definiują one atrybutów typu samej funkcji. Atrybut Thread ma wpływ tylko na dane. Atrybut owies ma wpływ tylko na funkcje. Atrybuty dllimport i dllexport mają wpływ na funkcje i dane.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Deklaracje i typy](../c-language/declarations-and-types.md)
