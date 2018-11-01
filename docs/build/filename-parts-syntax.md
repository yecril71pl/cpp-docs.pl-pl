---
title: Składnia nazwy pliku-części
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
ms.openlocfilehash: 89869ccaea2a9a5c3d16762fe49b72efc462e0ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552051"
---
# <a name="filename-parts-syntax"></a>Składnia nazwy pliku-części

Składnia nazwy pliku części w poleceniach reprezentuje składniki pierwszy zależna nazwa pliku, (które mogą być dorozumianych zależnych od ustawień lokalnych). Nazwa pliku składniki są dysku pliku, ścieżka, nazwa podstawowa i rozszerzenia w określony sposób, nie, ponieważ istnieje na dysku. Użyj **%s** do reprezentowania pełną nazwę pliku. Użyj **%&#124;**[*części*]**F** (kreska pionowa znak następuje symbol procentu) do reprezentowania części nazwy pliku, gdzie *części*może mieć zero lub więcej z następujących liter, w dowolnej kolejności.

|Litera|Opis|
|------------|-----------------|
|Żadna litera|Pełna nazwa (taka sama jak **%s**)|
|**d**|Dysk|
|**p**|Ścieżka|
|**f**|Nazwa podstawowa pliku|
|**e**|Rozszerzenie pliku|

Na przykład, jeśli nazwa pliku jest c:\prog.exe:

- %s będzie c:\prog.exe

- %&#124;F będzie c:\prog.exe

- %&#124;dF będzie c

- %&#124;pF będzie c:\

- %&#124;fF będzie programu

- %&#124;eF będzie exe

## <a name="see-also"></a>Zobacz też

[Polecenia w pliku reguł programu Make](../build/commands-in-a-makefile.md)