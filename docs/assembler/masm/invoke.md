---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: 853bc9cd22d866357a4cd2d695beccc3efc20acf
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703963"
---
# <a name="invoke-32-bit-masm"></a>INVOKE (32-bitowy MASM)

Wywołuje procedurę pod adresem podanym przez *wyrażenie*, przekazując argumenty na stosie lub w rejestrach zgodnie ze standardowymi konwencjami wywoływania typu języka. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> INVOKE — *wyrażenie* [[, *argumenty*]]

## <a name="remarks"></a>Uwagi

Każdy argument przesłany do procedury może być wyrażeniem, parą rejestru lub wyrażeniem adresu (wyrażenie poprzedzające `ADDR`).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>