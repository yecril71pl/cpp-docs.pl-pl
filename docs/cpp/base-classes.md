---
title: Klas bazowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a6d6494cc1ef371cfeb51647bc310a74ac68bfb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059215"
---
# <a name="base-classes"></a>Klasy podstawowe

Proces dziedziczenie powoduje utworzenie nowej klasy pochodnej, która składa się z elementów członkowskich klas podstawowych, a także żadnych nowych elementów członkowskich dodane w klasie pochodnej. W dziedziczenia wielokrotnego jest możliwe do utworzenia wykresu dziedziczenia gdzie tej samej klasy bazowej jest częścią więcej niż jednej z klas pochodnych. Na poniższej ilustracji przedstawiono taki wykres.

![Wiele wystąpień klasy bazowej](../cpp/media/vc38xn1.gif "vc38XN1") wiele wystąpień pojedyncza klasa bazowa

Na rysunku, połączyć reprezentacje składniki `CollectibleString` i `CollectibleSortable` są wyświetlane. Jednak klasy bazowej, `Collectible`, znajduje się w `CollectibleSortableString` za pośrednictwem `CollectibleString` ścieżki i `CollectibleSortable` ścieżki. Aby wyeliminować tę nadmiarowość, takich klas mogą być deklarowane jako wirtualne klasy bazowe, gdy są one dziedziczone.