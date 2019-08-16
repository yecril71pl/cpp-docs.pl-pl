---
title: Marshaling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 9963e261f26daa57cb58e30ffc404b431d781bfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492042"
---
# <a name="marshaling"></a>Marshaling

Technika COM kierująca umożliwia interfejsy uwidocznione przez obiekt w jednym procesie, który ma być używany w innym procesie. W obszarze kierowanie modelu COM udostępnia kod (lub używa kodu dostarczonego przez implementujący interfejs) zarówno do pakowania parametrów metody do formatu, który może być przenoszony między procesami (a także w sieci do procesów uruchomionych na innych maszynach) i rozpakowywania tych parametrów na drugim końcu. Analogicznie, COM musi wykonać te same kroki na zwracaniu z wywołania.

> [!NOTE]
>  Kierowanie nie jest zwykle konieczne, gdy interfejs dostarczony przez obiekt jest używany w tym samym procesie co obiekt. Jednak może być wymagana kierowanie między wątkami.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Szczegóły organizowania](/windows/win32/com/marshaling-details)
