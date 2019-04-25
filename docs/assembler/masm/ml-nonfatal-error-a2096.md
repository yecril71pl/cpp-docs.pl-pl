---
title: Błąd niekrytyczny ML A2096
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: e6b31afeff801e7128b5a76576e9eaa3398f68e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62202499"
---
# <a name="ml-nonfatal-error-a2096"></a>Błąd niekrytyczny ML A2096

**Segment, grupy lub rejestru segmentu oczekiwano**

Segment lub grupy był oczekiwany, ale nie został znaleziony.

Wystąpił jeden z następujących czynności:

- Lewy operand określony segment zastąpienia operatora (**:**) nie była segmentu rejestru (CS, DS, SS, ES, FS lub GS), nazwa grupy, nazwą segmentu lub wyrażenie segmentu.

- [PRZYJMIJ](../../assembler/masm/assume.md) dyrektywy podano rejestru segmentu, bez adresu nieprawidłowy segment, rejestr segmentu, grupy lub specjalne **PROSTEGO** grupy.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>