---
title: Definicje i konwencje
ms.date: 11/04/2016
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
ms.openlocfilehash: 0ff3f8b447e29f0da59405a7c0286d7a696b4613
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234440"
---
# <a name="definitions-and-conventions"></a>Definicje i konwencje

Terminale są punktami końcowymi w definicji składni. Inne rozwiązanie nie jest możliwe. Terminale obejmują zestaw słów zarezerwowanych i identyfikatorów zdefiniowanych przez użytkownika.

Nieterminale są symbolami zastępczymi w składni i są zdefiniowane w innym miejscu w tym podsumowaniu składni. Definicje mogą być cykliczne.

Opcjonalny składnik jest wskazywany przez <sub>wybór</sub>z indeksu. Na przykład:

> **{** *wyrażenie*{<sub>opt</sub> **}**

wskazuje opcjonalne wyrażenie ujęte w nawiasy klamrowe.

Konwencje składni używają różnych atrybutów czcionki dla różnych składników składni. Symbole i czcionki są następujące:

|Atrybut|Opis|
|---------------|-----------------|
|*nieterminal*|Typ kursywy oznacza nieterminale.|
|**const**|Terminale w pogrubieniu są literałami zarezerwowanymi i symbolami, które muszą zostać wprowadzone jako pokazane. Znaki w tym kontekście zawsze uwzględniają wielkość liter.|
|<sub>uszlachetniania</sub>|Nieterminale, po których następuje <sub>wybór</sub> , są zawsze opcjonalne.|
|domyślny krój czcionki|Znaki w zestawie opisany lub wymieniony w tym kroju pisma mogą być używane jako terminale w instrukcjach języka C.|

Jest to dwukropek (**:**) po wprowadzeniu definicji przez nieterminala. Definicje alternatywne są wyświetlane w oddzielnych wierszach, z wyjątkiem przypadków, gdy są poprzedzone wyrazami "one of".

## <a name="see-also"></a>Zobacz też

[Podsumowanie składni języka C](../c-language/c-language-syntax-summary.md)
