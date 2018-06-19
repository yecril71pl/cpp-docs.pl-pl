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
ms.openlocfilehash: 5a17aa8b4e2a98d3bda5d21ea84962791b8051dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295187"
---
# <a name="bscmake-warning-bk4504"></a>Ostrzeżenie BSCMAKE BK4504
plik zawiera za dużo odwołań; ignorowanie dalsze odwołań z tego źródła  
  
 Plik .cpp zawiera więcej niż 64 000 odwołania do symboli. Gdy BSCMAKE napotkał 64 000 odwołań w pliku, ignoruje wszystkie dodatkowe odwołania.  
  
 Aby rozwiązać ten problem, albo plik podzielony na dwie lub więcej plików, z których każda ma mniej niż 64 000 odwołania do symbolu, lub użyj `#pragma component(browser)` dyrektywy preprocesora do symboli limit, które są generowane dla danego odwołania. Aby uzyskać więcej informacji, zobacz [składnika](../../preprocessor/component.md).