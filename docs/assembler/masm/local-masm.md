---
title: LOKALNE (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8105bc8168ce28d468a1378c5cf7889907a7c9f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685066"
---
# <a name="local-masm"></a>LOCAL (MASM)

Pierwszy dyrektywą, wewnątrz makr **lokalnego** definiuje etykiety, które są unikatowe dla poszczególnych wystąpień tego makra.

## <a name="syntax"></a>Składnia

> LOKALNE *localname* [[, *localname*]]...

> LOKALNE *etykiety* [[[*liczba*]]] [[:*typu*]] [[, *etykiety* [[[*liczba*]]] [[ *Typ*]]]]...

## <a name="remarks"></a>Uwagi

W drugiej — dyrektywa w definicji procedury (**PROC**), **lokalnego** tworzy zmienne oparty na stosie, znajdujące się na czas trwania procedury. *Etykiety* może być prosta zmienna lub tablica zawierająca *liczba* elementów.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>