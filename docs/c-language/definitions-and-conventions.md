---
title: Definicje i konwencje
ms.date: 11/04/2016
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
ms.openlocfilehash: 9da9a566ef0b8d34a1a3d64dd2b8ce659194e6ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226382"
---
# <a name="definitions-and-conventions"></a>Definicje i konwencje

Terminale są punktami końcowymi w definicji składni. Inne rozwiązanie nie jest możliwe. Terminale obejmują zestaw słów zarezerwowanych i identyfikatorów zdefiniowanych przez użytkownika.

Nieterminale są symbolami zastępczymi w składni i są zdefiniowane w innym miejscu w tym podsumowaniu składni. Definicje mogą być cykliczne.

Opcjonalny składnik jest wskazywany przez <sub>wybór</sub>z indeksu. Przykład:

> **{** *wyrażenie*{<sub>opt</sub> **}**

wskazuje opcjonalne wyrażenie ujęte w nawiasy klamrowe.

Konwencje składni używają różnych atrybutów czcionki dla różnych składników składni. Symbole i czcionki są następujące:

|Atrybut|Opis|
|---------------|-----------------|
|*nieterminal*|Typ kursywy oznacza nieterminale.|
|**`const`**|Terminale w pogrubieniu są literałami zarezerwowanymi i symbolami, które muszą zostać wprowadzone jako pokazane. Znaki w tym kontekście zawsze uwzględniają wielkość liter.|
|<sub>uszlachetniania</sub>|Nieterminale, po których następuje <sub>wybór</sub> , są zawsze opcjonalne.|
|domyślny krój czcionki|Znaki w zestawie opisany lub wymieniony w tym kroju pisma mogą być używane jako terminale w instrukcjach języka C.|

Jest to dwukropek (**:**) po wprowadzeniu definicji przez nieterminala. Definicje alternatywne są wyświetlane w oddzielnych wierszach, z wyjątkiem przypadków, gdy są poprzedzone wyrazami "one of".

## <a name="see-also"></a>Zobacz także

[Podsumowanie składni języka C](../c-language/c-language-syntax-summary.md)
