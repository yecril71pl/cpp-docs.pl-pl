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
ms.workload: cplusplus
ms.openlocfilehash: 58a59b3141a8d7051aa7ece1bcb71dd960fabb18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-warning-bk4504"></a>Ostrzeżenie BSCMAKE BK4504
plik zawiera za dużo odwołań; ignorowanie dalsze odwołań z tego źródła  
  
 Plik .cpp zawiera więcej niż 64 000 odwołania do symboli. Gdy BSCMAKE napotkał 64 000 odwołań w pliku, ignoruje wszystkie dodatkowe odwołania.  
  
 Aby rozwiązać ten problem, albo plik podzielony na dwie lub więcej plików, z których każda ma mniej niż 64 000 odwołania do symbolu, lub użyj `#pragma component(browser)` dyrektywy preprocesora do symboli limit, które są generowane dla danego odwołania. Aby uzyskać więcej informacji, zobacz [składnika](../../preprocessor/component.md).