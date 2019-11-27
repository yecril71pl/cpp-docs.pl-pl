---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 73ef8bcc33087a56747b80f94482fcd6c50e3bf6
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399268"
---
# <a name="assume-32-bit-masm"></a>Przyjmij (32-bitowy MASM)

Włącza sprawdzanie błędów dla wartości rejestru. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> **Przyjmij**  *segregister* __:__ *name* ⟦ __,__ *segregister* __:__ *name*... ⟧\
> **Przyjmij**  *Rejestr*__danych:__ *wpisz* ⟦ __,__ *dataregister* __:__ *Type*... ⟧\
> **Przyjmij**  *Rejestr* __: błąd__ ⟦ __,__ *register* __: błąd__... ⟧\
> **Załóżmy, że** ⟦*register* __:__ ⟧**Nothing** ⟦ __,__ *register* __: Nothing__... ⟧

## <a name="remarks"></a>Uwagi

Po **założeniu** , że program asembler obserwuje zmiany wartości danego rejestru. **Błąd** powoduje wygenerowanie błędu, jeśli rejestr jest używany. **Nic nie** usuwa sprawdzania błędów rejestru. Można połączyć różne rodzaje założeń w jednej instrukcji.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)
