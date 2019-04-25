---
title: Błąd niekrytyczny ML A2008
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 7f85a3aabb7b1955cede912168dfc04618b8f2b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62201982"
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