---
title: _CIsin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: article
apiname:
- _CIsin
apilocation:
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- CIsin
- _CIsin
dev_langs:
- C++
helpviewer_keywords:
- _CIsin intrinsic
- CIsin intrinsic
ms.assetid: f215f39a-2341-4f1c-ba8e-cb522451ceb2
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0b06cd381bd93befd8fade4816ca4ead6b3ef9d
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="cisin"></a>_CIsin

Oblicza sinus wartość top w stosie liczb zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
void __cdecl _CIsin();
```

## <a name="remarks"></a>Uwagi

Ta wersja wewnętrznej [sin](../c-runtime-library/reference/sin-sinf-sinl.md) funkcja ma specjalne Konwencja wywoływania obsługującą przez kompilator. Przyspiesza wykonywanie, ponieważ uniemożliwia kopie generowany, a ułatwia alokacja rejestru.

Wartość wynikową spoczywa na wierzchu stosu zmiennoprzecinkowych.

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[SIN sinf —, sinl —](../c-runtime-library/reference/sin-sinf-sinl.md)<br/>
