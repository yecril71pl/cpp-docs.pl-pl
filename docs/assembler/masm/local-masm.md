---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 94af498865151ff5c49fac9dbc03de65c4ecb934
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327606"
---
# <a name="local-masm"></a>LOCAL (MASM)

Pierwszy dyrektywą, wewnątrz makr **lokalnego** definiuje etykiety, które są unikatowe dla poszczególnych wystąpień tego makra.

## <a name="syntax"></a>Składnia

> LOKALNE *localname* \[, *localname*]...
>
> LOKALNE *etykiety* \[ __\[__ *liczba*__]__ ] \[ __:__  *Typ*] \[ __,__ *etykiety* \[ __\[__ *liczba* __]__  ] \[ *typu*]]...

## <a name="remarks"></a>Uwagi

W drugiej — dyrektywa w definicji procedury (**PROC**), **lokalnego** tworzy zmienne oparty na stosie, znajdujące się na czas trwania procedury. *Etykiety* może być prosta zmienna lub tablica zawierająca *liczba* elementów.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>