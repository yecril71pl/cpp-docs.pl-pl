---
title: BIBLIOTEKA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- LIBRARY
dev_langs:
- C++
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43b14e8e8ff4871ba4319c7f4fac5545e72e710b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723557"
---
# <a name="library"></a>BIBLIOTEKA

/ ORDER informuje KONSOLIDACJĘ, aby utworzyć biblioteki DLL. W tym samym czasie LINK tworzy bibliotekę importu, chyba że używany jest plik .exp w kompilacji.

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>Uwagi

*Biblioteki* argument określa nazwę biblioteki DLL. Można również użyć [/OUT](../../build/reference/out-output-file-name.md) opcję konsolidatora, aby określić nazwę wyjściowego pliku DLL.

Podstawa =*adres* argument ustawia adres podstawowy, który korzysta z systemu operacyjnego można załadować biblioteki DLL. Argument ten zastępuje domyślną lokalizację biblioteki DLL 0x10000000. Zobacz opis [/BASE](../../build/reference/base-base-address.md) opcji szczegółowe informacje na temat adres podstawowy.

Pamiętaj, aby używać [/dll](../../build/reference/dll-build-a-dll.md) podczas kompilowania biblioteki DLL — opcja konsolidatora.

## <a name="see-also"></a>Zobacz też

[Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)