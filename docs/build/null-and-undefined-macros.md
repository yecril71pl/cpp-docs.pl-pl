---
title: Zerowe i niezdefiniowane makra | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 494a084ee5ba1da29c132aa632b647b37f305855
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="null-and-undefined-macros"></a>Makra niezdefiniowane oraz makra o wartości zerowej
Zarówno zerowe i niezdefiniowane makra Rozwiń do ciągów o wartości null, ale makra zdefiniowane jako ciąg pusty jest uznawany za zdefiniowane w przetwarzaniu wstępnym wyrażenia. Aby zdefiniować makro jako ciąg pusty, określ żadne znaki z wyjątkiem spacji ani karty po znaku równości (=) w wierszu polecenia lub pliku polecenia, a ciąg null lub definicji ująć w podwójny cudzysłów (""). Aby nie zdefiniowany makra, należy użyć **! UNDEF.** Aby uzyskać więcej informacji, zobacz [dyrektywy przetwarzania wstępnego pliku reguł programu make](../build/makefile-preprocessing-directives.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)