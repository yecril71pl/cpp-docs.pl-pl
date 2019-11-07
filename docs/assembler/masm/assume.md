---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 4bf8f0c41e9ce3e296cf201efd4fd9be2033cbdb
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73702470"
---
# <a name="assume-32-bit-masm"></a>Przyjmij (32-bitowy MASM)

Włącza sprawdzanie błędów dla wartości rejestru. (tylko 32-bitowy MASM).

## <a name="syntax"></a>Składnia

> Przyjmij *segregister*:*Nazwa* [[, *segregister*:*Nazwa*]]...<br/>
> Przyjmij *Rejestr*danych:*Typ* [[, *dataregister*:*Typ*]]...<br/>
> Przyjmij *Rejestr*: błąd [[, *register*: błąd]]...<br/>
> ZAŁÓŻMY [[*register*:]] Nothing [[, *register*: Nothing]]...

## <a name="remarks"></a>Uwagi

Po rozpoczęciu `ASSUME`, asembler obserwuje zmiany w wartościach danego rejestru. **Błąd** powoduje wygenerowanie błędu, jeśli rejestr jest używany. **Nic nie** usuwa sprawdzania błędów rejestru. Można połączyć różne rodzaje założeń w jednej instrukcji.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>