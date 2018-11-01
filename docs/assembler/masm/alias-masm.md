---
title: ALIAS (MASM)
ms.date: 08/30/2018
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: ab00092f410d34119e876db4562e6d0709743d79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483502"
---
# <a name="alias-masm"></a>ALIAS (MASM)

**ALIAS** tworzy dyrektywa alternatywną nazwę funkcji.  Dzięki temu można utworzyć wiele nazw dla funkcji lub tworzenie bibliotek, które umożliwiają łączący (LINK.exe) do mapowania funkcję starej do nowej funkcji.

## <a name="syntax"></a>Składnia

> ALIAS \< *alias*> = \< *rzeczywista nazwa*>

#### <a name="parameters"></a>Parametry

*Rzeczywista nazwa*<br/>
Rzeczywista nazwa funkcji lub procedury.  Nawiasy są wymagane.

*Alias*<br/>
Nazwa aliasu lub alternatywne.  Nawiasy są wymagane.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>