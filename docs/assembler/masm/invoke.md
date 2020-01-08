---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: 7a005e5e70a2696ca89fb0ad1a3ff02aab8ffe5a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317191"
---
# <a name="invoke"></a>INVOKE

(tylko 32-bitowy MASM). Wywołuje procedurę pod adresem podanym przez *wyrażenie*, przekazując argumenty na stosie lub w rejestrach zgodnie ze standardowymi konwencjami wywoływania typu języka.     

## <a name="syntax"></a>Składnia

> **Wywołaj** *wyrażenie* ⟦ __,__ *Argument* ... ⟧

## <a name="remarks"></a>Uwagi

Każdy argument, który przeszedł do procedury, może być wyrażeniem, parą rejestru lub wyrażeniem adresu (wyrażenie poprzedzające **ADR**).

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
