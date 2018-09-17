---
title: -SWAPRUN | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /swaprun
dev_langs:
- C++
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a93b854dba2855fa68bb3be163cecdcd3570df0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723102"
---
# <a name="swaprun"></a>/SWAPRUN

```
/SWAPRUN:{[!]NET|[!]CD}
```

## <a name="remarks"></a>Uwagi

Ta opcja edytuje obraz, aby poinformować system operacyjny, skopiować obraz do pliku wymiany, i uruchom je stamtąd. Użyj tej opcji dla obrazów, które znajdują się w sieci lub nośnikach wymiennych.

Można dodawać i usuwać kwalifikatory NET lub CD:

- NET wskazuje, że obraz, który znajduje się w sieci.

- Ciągłe dostarczanie wskazuje, że obraz, który znajduje się na dysku CD-ROM lub podobne nośnik wymienny.

- Użyj! NET i! Ciągłe dostarczanie do odwrotnego skutki NET i ciągłego wdrażania.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](../../build/reference/editbin-options.md)