---
title: TLBID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6324ec9a64a0d1c47dab8d1beee021f6c8752a96
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807981"
---
# <a name="tlbid"></a>tlbid

**Określonego język C++**

Umożliwia ładowanie bibliotek innych niż biblioteki typu podstawowego.

## <a name="syntax"></a>Składnia

```
tlbid(number)
```

### <a name="parameters"></a>Parametry

*Numer*<br/>
Liczba bibliotekę typów w `filename`.

## <a name="remarks"></a>Uwagi

Jeśli wiele bibliotek typów są wbudowane w pojedynczego pliku DLL, możliwe do załadowania biblioteki inne niż biblioteki typu podstawowego, za pomocą **tlbid**.

Na przykład:

```cpp
#import <MyResource.dll> tlbid(2)
```

jest równoważne:

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)