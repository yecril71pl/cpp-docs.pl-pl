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
ms.openlocfilehash: 6fbba50e56ae06dc3afb64582d4a131bba75a6c8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055856"
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