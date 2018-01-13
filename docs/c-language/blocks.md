---
title: Bloki | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60126db8e2a8f7fe9e56041c4f5b119df828958c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="blocks"></a>Bloki
Sekwencja deklaracji, definicje i instrukcje ujętą w nawiasy klamrowe nawiasy klamrowe (**{}**) jest nazywany "block". Istnieją dwa typy bloków w C. "Instrukcja złożona," instrukcję składa się z jednego lub więcej instrukcji (zobacz [złożonej instrukcji](../c-language/compound-statement-c.md)), jest jeden typ bloku. Pozostałych "definicji funkcji", składa się z złożonej instrukcji (treści funkcji) oraz powiązanych funkcji "header" (nazwa funkcji, zwracany typ i parametrów formalnych). Blok w ramach innych bloków jest uznawany za "zagnieżdżony."  
  
 Należy pamiętać, że podczas wszystkie instrukcje złożone są ujęte w nawiasy klamrowe, nie wszystkie elementy ujętą w nawiasy klamrowe nawiasy klamrowe stanowi złożonej instrukcji. Na przykład specyfikacje elementów tablicy, struktury lub wyliczenia może pojawiać się w obrębie nawiasów klamrowych, nie są one instrukcje złożone.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)