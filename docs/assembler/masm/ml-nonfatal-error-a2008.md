---
title: Błąd niekrytyczny ML A2008 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 774cf4c2a51bf084fb63e572cc99b0c8e3cba26f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679378"
---
# <a name="ml-nonfatal-error-a2008"></a>Błąd niekrytyczny ML A2008

**Błąd składni:**

Token w bieżącej lokalizacji spowodował błąd składni.

Jedną z następujących przyczyn:

- Prefiks kropka zostało dodane do lub pominięte dyrektywy.

- Słowa zarezerwowanego (takie jak **C** lub **rozmiar**) została użyta jako identyfikator.

- Instrukcję był używany, które nie były dostępne z bieżącego zaznaczenia procesor lub Koprocesor.

- Operator porównania czasu wykonywania (takie jak `==`) został użyty w instrukcji warunkowej zestawu, zamiast operator relacyjny (takie jak [EQ](../../assembler/masm/operator-eq.md)).

- Za mało argumentów zostało przekazane z instrukcji lub dyrektywy.

- Przestarzała dyrektywa został użyty.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>