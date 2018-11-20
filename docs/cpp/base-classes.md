---
title: Klasy podstawowe
ms.date: 11/19/2018
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
ms.openlocfilehash: 59c474f54ea439acf83cf6923eba6e167901dd37
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175619"
---
# <a name="base-classes"></a>Klasy podstawowe

Proces dziedziczenie powoduje utworzenie nowej klasy pochodnej, która składa się z elementów członkowskich klas podstawowych, a także żadnych nowych elementów członkowskich dodane w klasie pochodnej. W dziedziczenia wielokrotnego jest możliwe do utworzenia wykresu dziedziczenia gdzie tej samej klasy bazowej jest częścią więcej niż jednej z klas pochodnych. Na poniższej ilustracji przedstawiono taki wykres.

![Wiele wystąpień klasy bazowej](../cpp/media/vc38xn1.gif "wielu wystąpień klasy bazowej") <br/>
Wiele wystąpień pojedyncza klasa bazowa

Na rysunku, połączyć reprezentacje składniki `CollectibleString` i `CollectibleSortable` są wyświetlane. Jednak klasy bazowej, `Collectible`, znajduje się w `CollectibleSortableString` za pośrednictwem `CollectibleString` ścieżki i `CollectibleSortable` ścieżki. Aby wyeliminować tę nadmiarowość, takich klas mogą być deklarowane jako wirtualne klasy bazowe, gdy są one dziedziczone.