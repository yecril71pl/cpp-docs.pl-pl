---
title: -DYNAMICBASE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dynamicbase
dev_langs:
- C++
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 255123157da3f802eafaf26206598d54fea02335
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211690"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Określa, czy ma być generowany obraz wykonywalny, który może być losowo przebazowanych w czasie ładowania przy użyciu funkcji randomizacji (ASLR) adres miejsca układu systemu Windows, która została po raz pierwszy dostępny w Windows Vista.

## <a name="syntax"></a>Składnia

> **/ DYNAMICBASE**[**: NO**]

## <a name="remarks"></a>Uwagi

**Opcja/DynamicBase** opcja modyfikuje nagłówek *obrazu pliku wykonywalnego*, pliku .dll lub .exe, aby wskazać, czy aplikacja powinna być losowo przebazowanych w czasie ładowania i umożliwia wirtualnego adresu losowe alokacji, który ma wpływ na lokalizację w pamięci wirtualnej sterty, stosy i alokacjami systemu operacyjnego. **Opcja/DynamicBase** opcja dotyczy zarówno 32-bitowych i 64-bitowych obrazów. Obsługiwany jest ASLR w systemach Windows Vista i nowszych systemach operacyjnych. Opcja jest ignorowana przez starszych systemów operacyjnych.

Domyślnie **opcja/DynamicBase** jest włączona. Aby wyłączyć tę opcję, należy użyć **: No**. **Opcja/DynamicBase** opcja jest wymagana dla [/highentropyva](highentropyva-support-64-bit-aslr.md) opcję, aby mieć wpływ.

## <a name="see-also"></a>Zobacz także

- [Opcje EDITBIN](../../build/reference/editbin-options.md)
- [Poziom ochrony oprogramowania niezależnego dostawcy oprogramowania Windows](https://msdn.microsoft.com/library/bb430720.aspx)