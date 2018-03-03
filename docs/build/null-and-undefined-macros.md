---
title: Zerowe i niezdefiniowane makra | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9581b152057655c510f1cbcd4ab29ba8339070b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="null-and-undefined-macros"></a>Makra niezdefiniowane oraz makra o wartości zerowej
Zarówno zerowe i niezdefiniowane makra Rozwiń do ciągów o wartości null, ale makra zdefiniowane jako ciąg pusty jest uznawany za zdefiniowane w przetwarzaniu wstępnym wyrażenia. Aby zdefiniować makro jako ciąg pusty, określ żadne znaki z wyjątkiem spacji ani karty po znaku równości (=) w wierszu polecenia lub pliku polecenia, a ciąg null lub definicji ująć w podwójny cudzysłów (""). Aby nie zdefiniowany makra, należy użyć **! UNDEF.** Aby uzyskać więcej informacji, zobacz [dyrektywy przetwarzania wstępnego pliku reguł programu make](../build/makefile-preprocessing-directives.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)