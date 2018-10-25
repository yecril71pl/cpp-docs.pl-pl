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
ms.openlocfilehash: 6dcf63933a54983fcf98e35acce533670dc74ed4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070962"
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