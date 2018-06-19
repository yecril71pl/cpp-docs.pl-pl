---
title: Bloki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 309e6c017587a2dd3cdc80cd55ffec82751dedd3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380943"
---
# <a name="blocks"></a>Bloki
Sekwencja deklaracji, definicje i instrukcje ujętą w nawiasy klamrowe nawiasy klamrowe (**{}**) jest nazywany "block". Istnieją dwa typy bloków w C. "Instrukcja złożona," instrukcję składa się z jednego lub więcej instrukcji (zobacz [złożonej instrukcji](../c-language/compound-statement-c.md)), jest jeden typ bloku. Pozostałych "definicji funkcji", składa się z złożonej instrukcji (treści funkcji) oraz powiązanych funkcji "header" (nazwa funkcji, zwracany typ i parametrów formalnych). Blok w ramach innych bloków jest uznawany za "zagnieżdżony."  
  
 Należy pamiętać, że podczas wszystkie instrukcje złożone są ujęte w nawiasy klamrowe, nie wszystkie elementy ujętą w nawiasy klamrowe nawiasy klamrowe stanowi złożonej instrukcji. Na przykład specyfikacje elementów tablicy, struktury lub wyliczenia może pojawiać się w obrębie nawiasów klamrowych, nie są one instrukcje złożone.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)