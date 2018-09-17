---
title: Wykonywanie programu w przetwarzaniu wstępnym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2b0571e67e7c5d24cf31dce6fce548735cad966
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721464"
---
# <a name="executing-a-program-in-preprocessing"></a>Wykonywanie programu w przetwarzaniu wstępnym

Aby użyć kod zakończenia polecenia podczas przetwarzania wstępnego, należy określić polecenia, za pomocą argumenty w nawiasy kwadratowe ([]). Wszystkie makra zostaną rozwinięte przed wykonaniem polecenia. NMAKE zastępuje Specyfikacja polecenia z kodem zakończenia polecenia, którego można użyć do kontrolowania przetwarzania wstępnego w wyrażeniu.

## <a name="see-also"></a>Zobacz też

[Wyrażenia w przetwarzaniu wstępnym pliku reguł programu Make](../build/expressions-in-makefile-preprocessing.md)