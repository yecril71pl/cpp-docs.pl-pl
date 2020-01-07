---
title: ALIAS (MASM)
ms.date: 12/17/2019
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 5aef169c5632e74722438c63718ce5b783a8da09
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316606"
---
# <a name="alias"></a>ALIAS

Dyrektywa **aliasu** tworzy alternatywną nazwę dla funkcji.  Dzięki temu można utworzyć wiele nazw dla funkcji lub utworzyć biblioteki, które zezwalają konsolidatorowi (LINK. exe) na zamapowanie starej funkcji do nowej funkcji.

## <a name="syntax"></a>Składnia

> Alias **\<** _aliasu_ **> = \<** _rzeczywista nazwa_ **>**

#### <a name="parameters"></a>Parametry

*rzeczywista nazwa*\
Rzeczywista nazwa funkcji lub procedury.  Nawiasy kątowe są wymagane.

*alias*\
Nazwa alternatywna lub aliasu.  Nawiasy kątowe są wymagane.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
