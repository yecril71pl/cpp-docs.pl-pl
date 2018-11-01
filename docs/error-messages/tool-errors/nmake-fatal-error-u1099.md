---
title: Błąd krytyczny NMAKE U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 395f25d8d27bc5e9b6132c87390c8c3bc19b6cc4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631221"
---
# <a name="nmake-fatal-error-u1099"></a>Błąd krytyczny NMAKE U1099

przepełnienie stosu

Trwa przetwarzanie pliku reguł programu make jest zbyt złożona, bieżący alokacji stosu w NMAKE. NMAKE ma alokacji 0x3000 (12 KB).

Aby zwiększyć alokacji stosu w NMAKE, uruchom [editbin /stack](../../build/reference/stack.md) narzędzia z opcją większej stosu:

**editbin /STACK:reserve NMAKE. PLIK EXE**

gdzie *zarezerwować* jest większa niż bieżąca Alokacja stosu w NMAKE liczbą.