---
title: ". Ilk, pliki jako dane wejściowe konsolidatora | Dokumentacja firmy Microsoft"
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
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b91d229e1c607be1ed35685ab7bfdffe2271e16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ilk-files-as-linker-input"></a>Pliki .Ilk — Wejście konsolidatora
Podczas łączenia przyrostowo, LINK aktualizuje plik stanu .ilk utworzony podczas pierwszego konsolidowania przyrostowego. Ten plik ma taką samą nazwę podstawową jak pliku .exe lub .dll i ma .ilk rozszerzenia. Podczas kolejnych konsolidacji przyrostowej LINK aktualizuje plik .ilk. Jeśli brakuje pliku .ilk LINK wykonuje pełne łącza i tworzy nowy plik .ilk. Jeśli plik .ilk jest korzystanie z niej, LINK wykonuje nieprzyrostowa łącza. Aby uzyskać więcej informacji o konsolidowania przyrostowego, zobacz [przyrostowo łącza (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) opcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki wyjściowe LINK](../../build/reference/link-input-files.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)