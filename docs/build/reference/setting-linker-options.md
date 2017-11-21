---
title: Ustawianie opcji konsolidatora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b64b1dfd342598735124940d01b1bb4939242e10
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setting-linker-options"></a>Ustawianie opcji konsolidatora
Opcje konsolidatora można ustawić wewnątrz lub na zewnątrz środowiska programowania. Temat dla każdej opcji konsolidatora opisano, jak można ją ustawić w środowisku programistycznym. Zobacz [opcje konsolidatora](../../build/reference/linker-options.md) pełną listę.  
  
 Po uruchomieniu łącze poza Środowisko deweloperskie, można określić dane wejściowe w jeden lub więcej sposobów:  
  
-   Na [wiersza polecenia](../../build/reference/linker-command-line-syntax.md)  
  
-   Przy użyciu [pliki poleceń](../../build/reference/link-command-files.md)  
  
-   W [zmienne środowiskowe](../../build/reference/link-environment-variables.md)  
  
 Opcje procesów pierwszy LINK określony w zmiennej środowiskowej łącza, następuje opcje w kolejności, są one określone w wierszu polecenia i pliki poleceń. Opcja jest powtarzany różnych argumentów, pierwszeństwo ma ostatnią przetworzone.  
  
 Opcje odnoszą się do całego kompilacji; Brak opcji może odnosić się do określonych plików wejściowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie kompilacji C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)