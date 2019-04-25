---
title: ASSUME
ms.date: 08/30/2018
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 97a57cc8a1acccf70572ff963e496aa79fa3ab43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166467"
---
# <a name="assume"></a>ASSUME

Włącza sprawdzanie błędów dotyczących wartości rejestru.

## <a name="syntax"></a>Składnia

> PRZYJMIJ *segregister*:*nazwa* [[, *segregister*:*nazwa*]]...<br/>
> PRZYJMIJ *dataregister*:*typu* [[, *dataregister*:*typu*]]...<br/>
> PRZYJMIJ *zarejestrować*: błąd [[, *zarejestrować*: błąd]]...<br/>
> PRZYJMIJ [[*zarejestrować*:]] nic [[, *zarejestrować*: nie RÓB]]...

## <a name="remarks"></a>Uwagi

Po `ASSUME` zacznie obowiązywać, asembler obserwuje się zmian wartości danego rejestrów. **Błąd** generuje błąd, jeśli rejestr jest używany. **Nic nie** usuwa zarejestrować, sprawdzanie błędów. Można łączyć różnego rodzaju założenia w jednej instrukcji.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>