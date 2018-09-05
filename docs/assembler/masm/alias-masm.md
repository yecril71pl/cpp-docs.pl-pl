---
title: ALIAS (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6a977d35040d8ca25cd3bd4ae4def233092b37a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691065"
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