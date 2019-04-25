---
title: Rozszerzone atrybuty klasy magazynu języka C
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
ms.openlocfilehash: 9b0c8b60dab3229d5d5c162f7bafc959fa2558f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325887"
---
# <a name="c-extended-storage-class-attributes"></a>Rozszerzone atrybuty klasy magazynu języka C

**Microsoft Specific**

Bardziej aktualnych informacji na ten temat można znaleźć w obszarze [__declspec (C++ odwołania)](../cpp/declspec.md).

Składnia atrybutu rozszerzonego upraszcza i standaryzuje rozszerzenia specyficzne dla firmy Microsoft dla języka C. Atrybuty klasy magazynowania korzystających ze składni atrybutów rozszerzonych obejmują wątku "naked", dllimport i dllexport.

Składnia atrybutów rozszerzonych służących do określania informacji klasy magazynowania wykorzystuje słowo kluczowe __declspec, który określa, czy wystąpienie danego typu ma być przechowywane z atrybutem klasy magazynowania specyficzne dla firmy Microsoft (wątek "naked" dllimport i dllexport). Przykłady innych modyfikatorów klasy magazynowania słów statyczne i zewnętrzne. Jednak te słowa kluczowe są częścią standardu ANSI C i jako takie nie są objęte składnią atrybutów rozszerzonych.

## <a name="syntax"></a>Składnia

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *extended-decl modyfikator seq* **)**  / \* Specific firmy Microsoft \*/

*extended-decl-modifier-seq*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*extended-decl-modifier*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Wątek**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

Spacja oddziela Modyfikatory deklaracji. Należy pamiętać, że *extended-decl modyfikator seq* może być pusta; w takim przypadku __declspec nie ma wpływu.

Wątek "naked" dllimport i dllexport atrybuty klasy magazynu są właściwości tylko dla deklaracji danych lub funkcji, do której są stosowane; nie są ponownie zdefiniować atrybuty typu sama funkcja. Atrybut wątku wpływa na tylko dane. Atrybut "naked" dotyczy tylko funkcji. Atrybuty dllimport i dllexport wpływają na funkcje i dane.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)
