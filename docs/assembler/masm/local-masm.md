---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c8ea49b9862159a5a56bfb3d2c3cd0c1f4cd7413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596875"
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