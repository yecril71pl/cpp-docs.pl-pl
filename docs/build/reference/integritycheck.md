---
title: / INTEGRITYCHECK | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /INTEGRITYCHECK
dev_langs:
- C++
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99caec18162a7506b8b7a467eb7374b6fe4a38d9
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Określa, że podpis cyfrowy obraz binarny, muszą zostać sprawdzone w czasie ładowania.

> **/ INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>Uwagi

W nagłówku pliku DLL lub pliku wykonywalnego ta opcja umożliwia ustawienie Flaga, która wymaga sprawdzenia podpisu cyfrowego, przez Menedżera pamięci można załadować obrazu w systemie Windows. Wersje systemu Windows starszych niż Windows Vista zignorować tę flagę. Tę opcję należy wybrać dla 64-bitowych bibliotek DLL, zaimplementować kod trybu jądra, które jest zalecane w przypadku wszystkich sterowników urządzeń. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące podpisywania kodu w trybie jądra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](../../build/reference/editbin-options.md)  
