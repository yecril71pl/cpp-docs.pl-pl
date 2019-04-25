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

Terminale to punkty końcowe w definicji składni. Możliwe jest inne rozwiązanie. Terminale obejmują zbiór słów zastrzeżonych oraz identyfikatorów zdefiniowanych przez użytkownika.

Symboli nieterminalnych są symbole zastępcze w składni i są definiowane w innych miejscach w tej składni podsumowania. Definicje mogą być cykliczne.

Opcjonalny składnik jest wskazywany przez indeksem <sub>zoptymalizowany pod kątem</sub>. Na przykład

> **{** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **}**

Określa opcjonalne wyrażenie ujęte w nawiasy klamrowe.

Konwencje składni Użyj atrybutów czcionkę dla różnych składników składni. Symbole i czcionki są następujące:

|Atrybut|Opis|
|---------------|-----------------|
|*nieterminalnych*|Kursywa wskazuje symboli nieterminalnych.|
|**const**|Terminale czcionką pogrubioną są literału wyrazy zastrzeżone i symboli, które należy wprowadzić, jak pokazano. Znaki w tym kontekście są zawsze z uwzględnieniem wielkości liter.|
|<sub>opt</sub>|Następuje symboli nieterminalnych <sub>zoptymalizowany pod kątem</sub> zawsze są opcjonalne.|
|krój czcionki domyślnej|Znaków w zestawie opisane lub wymienionych w tej czcionce może służyć jako terminale w instrukcjach języka C.|

Dwukropek (**:**) po nieterminalnych wprowadza jego definicji. Alternatywne definicje są wymienione w osobnych wierszach, z wyjątkiem, gdy poprzedzone znakiem słowa "poszczególnych."

## <a name="see-also"></a>Zobacz także

[Podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md)
