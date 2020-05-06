---
title: Wypełnienie i wyrównanie struktur członkowskich
ms.date: 10/18/2018
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
ms.openlocfilehash: 0f9c70ed074a11800b707aa48ec8e0e2f8b4f999
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325367"
---
# <a name="padding-and-alignment-of-structure-members"></a>Wypełnienie i wyrównanie struktur członkowskich

**3.5.2.1 ANSI** Uzupełnienie i wyrównanie elementów członkowskich struktur oraz tego, czy pole bitowe może obsłużyć granicę jednostki magazynu

Elementy członkowskie struktur są przechowywane sekwencyjnie, w kolejności, w której były zadeklarowane: pierwszy element członkowski ma najniższy adres pamięci, a ostatni element członkowski – najwyższy.

Każdy obiekt danych ma wymaganie wyrównania. Wyrównanie — wymaganie dla wszystkich danych z wyjątkiem struktur, Unii i tablic jest rozmiarem obiektu lub bieżącym rozmiarem pakowania (określonym przy użyciu/ZP lub pragma, w `pack` zależności od tego, co jest mniejsze). W przypadku struktur, Unii i tablic, dopasowanie-wymaganie jest największym wymaganiem dla elementów członkowskich. Każdy obiekt ma przydzieloną przesunięcie, aby

Wyrównanie *przesunięcia* **%** *— wymaganie* **= = 0**

Sąsiadujące pola bitowe są pakowane w takie same 1-, 2- lub 4-bajtowe jednostki alokacji, jeśli typy całkowite mają taki sam rozmiar i jeśli następne pole bitowe pasuje do bieżącej jednostki alokacji bez przekraczania granicy nałożonej przez wspólne wymagania wyrównania pól bitowych.

## <a name="see-also"></a>Zobacz też

[Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)
