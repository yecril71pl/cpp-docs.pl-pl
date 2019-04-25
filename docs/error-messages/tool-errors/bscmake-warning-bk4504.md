---
title: Ostrzeżenie BSCMAKE BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 7ffcb7c2e6ae512006ccd29c87b05c53fdfcaef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279306"
---
# <a name="bscmake-warning-bk4504"></a>Ostrzeżenie BSCMAKE BK4504

plik zawiera zbyt dużo odwołań; ignorowanie dalsze odwołań z tego źródła

Plik CPP zawiera ponad 64 000 odwołań do symboli. W przypadku BSCMAKE ma 64 000 odwołań w pliku ignoruje wszystkie dalsze odwołania.

Aby rozwiązać ten problem, plik jest podzielony na dwie lub więcej plików, z których każdy ma mniej niż 64 000 odwołania do symbolu lub użyj `#pragma component(browser)` dyrektywy preprocesora limit symbole, które są generowane dla danego odwołania. Aby uzyskać więcej informacji, zobacz [składnika](../../preprocessor/component.md).