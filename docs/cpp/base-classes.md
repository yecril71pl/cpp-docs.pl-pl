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
ms.openlocfilehash: f1375cee34266b8d751e9c8d88fb22ce56f6c044
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407991"
---
# <a name="base-classes"></a>Klasy podstawowe
Proces dziedziczenie powoduje utworzenie nowej klasy pochodnej, która składa się z elementów członkowskich klas podstawowych, a także żadnych nowych elementów członkowskich dodane w klasie pochodnej. W dziedziczenia wielokrotnego jest możliwe do utworzenia wykresu dziedziczenia gdzie tej samej klasy bazowej jest częścią więcej niż jednej z klas pochodnych. Na poniższej ilustracji przedstawiono taki wykres.  
  
 ![Wiele wystąpień klasy bazowej](../cpp/media/vc38xn1.gif "vc38XN1")  
Wiele wystąpień pojedyncza klasa bazowa  
  
 Na rysunku, połączyć reprezentacje składniki `CollectibleString` i `CollectibleSortable` są wyświetlane. Jednak klasy bazowej, `Collectible`, znajduje się w `CollectibleSortableString` za pośrednictwem `CollectibleString` ścieżki i `CollectibleSortable` ścieżki. Aby wyeliminować tę nadmiarowość, takich klas mogą być deklarowane jako wirtualne klasy bazowe, gdy są one dziedziczone.  