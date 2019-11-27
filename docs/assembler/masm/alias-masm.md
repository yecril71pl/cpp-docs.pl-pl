---
title: ALIAS (MASM)
ms.date: 08/30/2018
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 274ac451005015b2693d8674673af574ec781bdc
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399289"
---
# <a name="alias-masm"></a>ALIAS (MASM)

Dyrektywa **aliasu** tworzy alternatywną nazwę dla funkcji.  Dzięki temu można utworzyć wiele nazw dla funkcji lub utworzyć biblioteki, które zezwalają konsolidatorowi (LINK. exe) na zamapowanie starej funkcji do nowej funkcji.

## <a name="syntax"></a>Składnia

> Alias **\<** _aliasu_ **> = \<** _rzeczywista nazwa_ **>**

#### <a name="parameters"></a>Parametry

*rzeczywista nazwa*\
Rzeczywista nazwa funkcji lub procedury.  Nawiasy kątowe są wymagane.

*alias*\
Nazwa alternatywna lub aliasu.  Nawiasy kątowe są wymagane.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)
