---
title: "Ostrzeżenie BSCMAKE BK4504 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK4504
dev_langs: C++
helpviewer_keywords: BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f7f6d854fbd74d9ca05ba6797bbd57db52b7a70e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bscmake-warning-bk4504"></a>Ostrzeżenie BSCMAKE BK4504
plik zawiera za dużo odwołań; ignorowanie dalsze odwołań z tego źródła  
  
 Plik .cpp zawiera więcej niż 64 000 odwołania do symboli. Gdy BSCMAKE napotkał 64 000 odwołań w pliku, ignoruje wszystkie dodatkowe odwołania.  
  
 Aby rozwiązać ten problem, albo plik podzielony na dwie lub więcej plików, z których każda ma mniej niż 64 000 odwołania do symbolu, lub użyj `#pragma component(browser)` dyrektywy preprocesora do symboli limit, które są generowane dla danego odwołania. Aby uzyskać więcej informacji, zobacz [składnika](../../preprocessor/component.md).