---
title: Mapowania zmiennych globalnych i stałych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
dev_langs:
- C++
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94cee77f82f850560cc5fe50e13b85c58b7187ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077855"
---
# <a name="constant-and-global-variable-mappings"></a>Mapowania zmiennych globalnych i stałych

Te — stała zwykłego tekstu, zmienna globalna i mapowania typu Standardowy są definiowane w TCHAR. Godz. i są zależne od tego, czy stałej `_UNICODE` lub `_MBCS` został zdefiniowany w programach.

### <a name="generic-text-constant-and-global-variable-mappings"></a>Mapowania zwykłego tekstu globalnych i stałych zmiennych

|— Zwykły tekst — nazwa obiektu|SBCS (_UNICODE, _MBCS nie zdefiniowano)|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TEOF`|`EOF`|`EOF`|`WEOF`|
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="see-also"></a>Zobacz też

[Mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md)<br/>
[Mapowania typu danych](../c-runtime-library/data-type-mappings.md)<br/>
[Mapowania procedur](../c-runtime-library/routine-mappings.md)<br/>
[Przykładowy ogólny program tekstowy](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Mapowania zwykłego tekstu](../c-runtime-library/using-generic-text-mappings.md)