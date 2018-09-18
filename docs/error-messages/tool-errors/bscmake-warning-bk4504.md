---
title: Ostrzeżenie BSCMAKE BK4504 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4504
dev_langs:
- C++
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a2da8903dade37faf3b14175b65f3169efd908
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049774"
---
# <a name="bscmake-warning-bk4504"></a>Ostrzeżenie BSCMAKE BK4504

plik zawiera zbyt dużo odwołań; ignorowanie dalsze odwołań z tego źródła

Plik CPP zawiera ponad 64 000 odwołań do symboli. W przypadku BSCMAKE ma 64 000 odwołań w pliku ignoruje wszystkie dalsze odwołania.

Aby rozwiązać ten problem, plik jest podzielony na dwie lub więcej plików, z których każdy ma mniej niż 64 000 odwołania do symbolu lub użyj `#pragma component(browser)` dyrektywy preprocesora limit symbole, które są generowane dla danego odwołania. Aby uzyskać więcej informacji, zobacz [składnika](../../preprocessor/component.md).