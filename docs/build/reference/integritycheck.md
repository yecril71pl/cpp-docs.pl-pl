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
ms.openlocfilehash: 062ce019fe1b622661be880d8a06eac9c5971103
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709206"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Określa, czy podpis cyfrowy obrazu binarnego musi być zaznaczone w czasie ładowania.

> **/ INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>Uwagi

W nagłówku pliku DLL lub pliku wykonywalnego ta opcja ustawia flagę, która wymaga sprawdzenia podpisu cyfrowego przez Menedżera pamięci w celu załadowania obrazu w Windows. Wersje Windows przed Windows Vista, ignorują tę flagę. Tę opcję należy ustawić dla 64-bitowych bibliotek DLL, które implementują kod trybu jądra i jest zalecana dla wszystkich sterowników urządzeń. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące podpisywania kodu trybu jądra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](../../build/reference/editbin-options.md)
