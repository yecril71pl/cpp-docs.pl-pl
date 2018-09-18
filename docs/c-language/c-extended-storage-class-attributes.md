---
title: Rozszerzone atrybuty klasy magazynu języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0fd89e21b10d241ea035e8c9b9c8ac8e5c3ee9cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106088"
---
# <a name="c-extended-storage-class-attributes"></a>Rozszerzone atrybuty klasy magazynu języka C

**Microsoft Specific**

Bardziej aktualnych informacji na ten temat można znaleźć w obszarze [__declspec (odwołanie w języku C++)](../cpp/declspec.md).

Składnia atrybutu rozszerzonego upraszcza i standaryzuje rozszerzenia specyficzne dla firmy Microsoft dla języka C. Atrybuty klasy magazynowania korzystających ze składni atrybutów rozszerzonych obejmują wątku "naked", dllimport i dllexport.

Składnia atrybutów rozszerzonych służących do określania informacji klasy magazynowania wykorzystuje słowo kluczowe __declspec, który określa, czy wystąpienie danego typu ma być przechowywane z atrybutem klasy magazynowania specyficzne dla firmy Microsoft (wątek "naked" dllimport i dllexport). Przykłady innych modyfikatorów klasy magazynowania słów statyczne i zewnętrzne. Jednak te słowa kluczowe są częścią standardu ANSI C i jako takie nie są objęte składnią atrybutów rozszerzonych.

## <a name="syntax"></a>Składnia

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *extended-decl modyfikator seq* **)**  / \* Specific firmy Microsoft \*/

*rozszerzony decl modyfikator seq*:&nbsp; &nbsp; &nbsp; &nbsp; / \* Specific firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony decl modyfikator*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony decl modyfikator seq* *extended-decl — modyfikator*

*rozszerzony decl modyfikator*:&nbsp; &nbsp; &nbsp; &nbsp; / \* Specific firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Wątek**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"naked"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**DllImport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

Spacja oddziela Modyfikatory deklaracji. Należy pamiętać, że *extended-decl modyfikator seq* może być pusta; w takim przypadku __declspec nie ma wpływu.

Wątek "naked" dllimport i dllexport atrybuty klasy magazynu są właściwości tylko dla deklaracji danych lub funkcji, do której są stosowane; nie są ponownie zdefiniować atrybuty typu sama funkcja. Atrybut wątku wpływa na tylko dane. Atrybut "naked" dotyczy tylko funkcji. Atrybuty dllimport i dllexport wpływają na funkcje i dane.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Deklaracje i typy](../c-language/declarations-and-types.md)