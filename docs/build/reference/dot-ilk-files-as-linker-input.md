---
title: . Ilk, pliki jako dane wejściowe konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01fea585b86114373017b6d73948cb1438b7185e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371687"
---
# <a name="ilk-files-as-linker-input"></a>Pliki .Ilk — Wejście konsolidatora
Podczas łączenia przyrostowo, LINK aktualizuje plik stanu .ilk utworzony podczas pierwszego konsolidowania przyrostowego. Ten plik ma taką samą nazwę podstawową jak pliku .exe lub .dll i ma .ilk rozszerzenia. Podczas kolejnych konsolidacji przyrostowej LINK aktualizuje plik .ilk. Jeśli brakuje pliku .ilk LINK wykonuje pełne łącza i tworzy nowy plik .ilk. Jeśli plik .ilk jest korzystanie z niej, LINK wykonuje nieprzyrostowa łącza. Aby uzyskać więcej informacji o konsolidowania przyrostowego, zobacz [przyrostowo łącza (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) opcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki wyjściowe LINK](../../build/reference/link-input-files.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)