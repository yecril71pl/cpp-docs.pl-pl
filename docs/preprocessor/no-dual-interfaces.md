---
title: no_dual_interfaces — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_dual_interfaces
dev_langs:
- C++
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eb26790a46f46638e4a4180ee2209efefda201c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432220"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Określonego język C++**  
  
Zmienia sposób, kompilator generuje funkcje otoki dla metod podwójnego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
no_dual_interfaces  
```  
  
## <a name="remarks"></a>Uwagi  
 
Zwykle otoki wywoła metodę przez tabelę funkcji wirtualnych dla interfejsu. Za pomocą **no_dual_interfaces —**, zamiast tego wywołania otoki `IDispatch::Invoke` było wywołanie metody.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)