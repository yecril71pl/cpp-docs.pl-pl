---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: a74a5336e626f561f1fc61e866792ce193332d84
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316541"
---
# <a name="assume"></a>ASSUME

Włącza sprawdzanie błędów dla wartości rejestru. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> **Przyjmij**  *segregister* __:__ *name* ⟦ __,__ *segregister* __:__ *name*... ⟧\
> **Przyjmij**  *Rejestr*__danych:__ *wpisz* ⟦ __,__ *dataregister* __:__ *Type*... ⟧\
> **Przyjmij**  *Rejestr* __: błąd__ ⟦ __,__ *register* __: błąd__... ⟧\
> **Załóżmy, że** ⟦*register* __:__ ⟧**Nothing** ⟦ __,__ *register* __: Nothing__... ⟧

## <a name="remarks"></a>Uwagi

Po **założeniu** , że program asembler obserwuje zmiany wartości danego rejestru. **Błąd** powoduje wygenerowanie błędu, jeśli rejestr jest używany. **Nic nie** usuwa sprawdzania błędów rejestru. Można połączyć różne rodzaje założeń w jednej instrukcji.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
