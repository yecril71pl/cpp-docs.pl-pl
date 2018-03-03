---
title: Podstawowa klasy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0a83507d89c17aab363f986dab3ff4d84c4c916
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="base-classes"></a>Klasy podstawowe
Proces dziedziczenia tworzy nowe klasy pochodnej, która składa się z elementów członkowskich klasy podstawowej oraz wszelkie nowe elementy członkowskie dodane przez klasy pochodnej. W dziedziczenia wielokrotnego jest możliwość utworzenia Wykres dziedziczenia gdzie tej samej klasy podstawowej wchodzi w skład więcej niż jednej z klas pochodnych. Na poniższej ilustracji przedstawiono takie wykresu.  
  
 ![Wiele wystąpień klasy podstawowej](../cpp/media/vc38xn1.gif "vc38XN1")  
Wiele wystąpień tej samej klasy podstawowej  
  
 Na rysunku obrazkami reprezentacje składniki `CollectibleString` i `CollectibleSortable` są wyświetlane. Jednak klasy podstawowej `Collectible`, znajduje się w `CollectibleSortableString` za pośrednictwem `CollectibleString` ścieżki i `CollectibleSortable` ścieżki. Aby wyeliminować ten nadmiarowość, takich klas mogą być deklarowane jako wirtualne klasy podstawowe, gdy są one dziedziczone.  
  
