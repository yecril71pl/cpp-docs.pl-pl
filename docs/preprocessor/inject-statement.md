---
title: inject_statement — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27b35c10e9e1953dc45dee1caf61d2e58c38d02d
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808646"
---
# <a name="injectstatement"></a>inject_statement

**Określonego język C++**

Wstawia jej argument jako tekst źródłowy do nagłówka biblioteki typów.

## <a name="syntax"></a>Składnia

```
inject_statement("source_text")
```

### <a name="parameters"></a>Parametry

*source_text*<br/>
Tekst źródłowy, który ma zostać wstawiony do pliku nagłówka biblioteki typów.

## <a name="remarks"></a>Uwagi

Tekst zostanie umieszczony na początku deklaracji przestrzeni nazw, który otacza zawartość biblioteki typów w pliku nagłówkowym.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)