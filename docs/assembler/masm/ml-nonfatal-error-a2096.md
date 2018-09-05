---
title: Błąd niekrytyczny ML A2096 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2096
dev_langs:
- C++
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f4ef76dca10b1208a931bc3e1cc09d82a639d2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679601"
---
# <a name="ml-nonfatal-error-a2096"></a>Błąd niekrytyczny ML A2096

**Segment, grupy lub rejestru segmentu oczekiwano**

Segment lub grupy był oczekiwany, ale nie został znaleziony.

Wystąpił jeden z następujących czynności:

- Lewy operand określony segment zastąpienia operatora (**:**) nie była segmentu rejestru (CS, DS, SS, ES, FS lub GS), nazwa grupy, nazwą segmentu lub wyrażenie segmentu.

- [PRZYJMIJ](../../assembler/masm/assume.md) dyrektywy podano rejestru segmentu, bez adresu nieprawidłowy segment, rejestr segmentu, grupy lub specjalne **PROSTEGO** grupy.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>