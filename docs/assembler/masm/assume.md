---
title: ZAŁÓŻMY | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ASSUME
dev_langs:
- C++
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a0e43548292d2ffecbebdaead6aa12d6dacc352
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693811"
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