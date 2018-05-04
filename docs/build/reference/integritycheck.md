---
title: / INTEGRITYCHECK | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: 4b0adf9add2d191ae89aec0a5d756ade8e9f7725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Określa, że podpis cyfrowy obraz binarny, muszą zostać sprawdzone w czasie ładowania.

> **/ INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>Uwagi

W nagłówku pliku DLL lub pliku wykonywalnego ta opcja umożliwia ustawienie Flaga, która wymaga sprawdzenia podpisu cyfrowego, przez Menedżera pamięci można załadować obrazu w systemie Windows. Wersje systemu Windows starszych niż Windows Vista zignorować tę flagę. Tę opcję należy wybrać dla 64-bitowych bibliotek DLL, zaimplementować kod trybu jądra, które jest zalecane w przypadku wszystkich sterowników urządzeń. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące podpisywania kodu w trybie jądra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](../../build/reference/editbin-options.md)  
