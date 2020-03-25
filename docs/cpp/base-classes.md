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
ms.openlocfilehash: 50bddef3ea1ee1462d8cf115c0980270c8deab25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181476"
---
# <a name="base-classes"></a>Klasy podstawowe

Proces dziedziczenia tworzy nową klasę pochodną, która składa się z elementów członkowskich klasy podstawowej (ES) i nowych elementów członkowskich dodanych przez klasę pochodną. W przypadku wielokrotnego dziedziczenia możliwe jest konstruowanie wykresu dziedziczenia, gdzie taka sama klasa bazowa jest częścią więcej niż jednej klasy pochodnej. Na poniższej ilustracji przedstawiono ten wykres.

![Wiele wystąpień klasy bazowej](../cpp/media/vc38xn1.gif "Wiele wystąpień klasy bazowej") <br/>
Wiele wystąpień pojedynczej klasy podstawowej

Na rysunku przedstawiono ilustrację obrazkową składników `CollectibleString` i `CollectibleSortable`. Jednak Klasa bazowa, `Collectible`, jest w `CollectibleSortableString` za pomocą ścieżki `CollectibleString` i ścieżki `CollectibleSortable`. Aby wyeliminować tę nadmiarowość, takie klasy mogą być deklarowane jako wirtualne klasy bazowe, gdy są dziedziczone.
