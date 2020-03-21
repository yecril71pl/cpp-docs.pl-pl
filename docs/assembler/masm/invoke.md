---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: ba1377359ba9bc960e5d7d2a55df15adfe0d5d33
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076220"
---
# <a name="invoke"></a>INVOKE

(tylko 32-bitowy MASM). Wywołuje procedurę pod adresem podanym przez *wyrażenie*, przekazując argumenty na stosie lub w rejestrach zgodnie ze standardowymi konwencjami wywoływania typu języka.

## <a name="syntax"></a>Składnia

> **Wywołaj** *wyrażenie* ⟦ __,__ *Argument* ... ⟧

## <a name="remarks"></a>Uwagi

Każdy argument, który przeszedł do procedury, może być wyrażeniem, parą rejestru lub wyrażeniem adresu (wyrażenie poprzedzające **ADR**).

## <a name="see-also"></a>Zobacz też

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
