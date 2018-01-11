---
title: Deklaracje i definicje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- local declarations
- function definitions, function declarations
- declaring functions, function definitions
- internal declarations
- external declarations
- function prototypes, basics
- external linkage, function declarations
- declaring functions
ms.assetid: 43fd98eb-7441-4473-a5d9-fc88c75577f7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 65be3d2e59a9d672db18ba332d608fdf031f16e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="function-declarations-and-definitions"></a>Deklaracje i definicje funkcji
Prototypy funkcji ustanowić nazwę funkcji, jego typ zwracany i typ i numer jego parametrów formalnych. Definicja funkcji zawiera treść funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Deklaracje zarówno funkcja i zmienna może występować wewnątrz lub na zewnątrz definicji funkcji. Żadnych deklaracji w definicji funkcji jest nazywany pojawiają się na poziomie "internal" lub "local". Deklaracja poza wszystkie definicje funkcji jest nazywany pojawiają się na poziomie "plik zakresu" lub "zewnętrzne" "globalne". Definicje zmiennych, takich jak deklaracje, może występować na poziomie wewnętrznym (w ramach definicji funkcji) lub na poziomie zewnętrzne (poza wszystkie definicje funkcji). Definicje funkcji są zawsze wykonywane na poziomie zewnętrznych. Definicje funkcji są omówione w dalszych [definicje funkcji](../c-language/c-function-definitions.md). Prototypy funkcji są objęte [prototypy funkcji](../c-language/function-prototypes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)