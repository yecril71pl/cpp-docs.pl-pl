---
title: Wypełnienie i wyrównanie struktur członkowskich
ms.date: 10/18/2018
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
ms.openlocfilehash: a560c7b9491c22d16866c4fa32f80d16ca38d90a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541287"
---
# <a name="padding-and-alignment-of-structure-members"></a>Wypełnienie i wyrównanie struktur członkowskich

**ANSI 3.5.2.1** wypełnienie i wyrównanie składowych struktur i tego, czy pole bitowe mogą wokół granicy jednostki magazynu

Elementy członkowskie struktur są przechowywane sekwencyjnie, w kolejności, w której były zadeklarowane: pierwszy element członkowski ma najniższy adres pamięci, a ostatni element członkowski – najwyższy.

Każdy obiekt danych posiada wymóg wyrównania. Wymóg wyrównania dla wszystkich danych z wyjątkiem struktur, Unii i tablice jest rozmiar obiektu lub bieżącego rozmiarem pakowania (określony za pomocą obu/ZP lub `pack` pragma, ta wartość jest mniejsza). Struktury, Unii i tablice wymóg wyrównania jest największy wymóg wyrównania składowych. Każdy obiekt jest przydzielany przesunięcie tak, aby

*Przesunięcie* **%** *wymóg wyrównania* **== 0**

Sąsiadujące pola bitowe są pakowane w takie same 1-, 2- lub 4-bajtowe jednostki alokacji, jeśli typy całkowite mają taki sam rozmiar i jeśli następne pole bitowe pasuje do bieżącej jednostki alokacji bez przekraczania granicy nałożonej przez wspólne wymagania wyrównania pól bitowych.

## <a name="see-also"></a>Zobacz też

[Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)