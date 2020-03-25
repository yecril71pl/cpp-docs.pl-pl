---
title: Ostrzeżenie BSCMAKE BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 57858827439ac8cc11e3718d7a484124ae8a6d74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197447"
---
# <a name="bscmake-warning-bk4504"></a>Ostrzeżenie BSCMAKE BK4504

plik zawiera zbyt wiele odwołań; ignorowanie dalszych odwołań z tego źródła

Plik. cpp zawiera więcej niż 64 000 odwołań do symboli. Gdy BSCMAKE napotkała odwołania do 64 000 w pliku, ignoruje wszystkie dalsze odwołania.

Aby rozwiązać ten problem, należy podzielić plik na co najmniej dwa pliki, z których każdy ma mniej niż 64 000 odwołań do symboli lub użyć dyrektywy preprocesora `#pragma component(browser)`, aby ograniczyć symbole, które są generowane dla określonych odwołań. Aby uzyskać więcej informacji, zobacz [składnik](../../preprocessor/component.md).
