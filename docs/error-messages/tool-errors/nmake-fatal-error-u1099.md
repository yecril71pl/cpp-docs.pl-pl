---
title: Błąd krytyczny NMAKE U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: c963180059a48d9aa0b09103df1ed54f82b8a2f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193397"
---
# <a name="nmake-fatal-error-u1099"></a>Błąd krytyczny NMAKE U1099

przepełnienie stosu

Przetwarzany plik reguł programu make był zbyt skomplikowany dla bieżącego przydziału stosu w NMAKE. NMAKE ma alokację 0x3000 (12K).

Aby zwiększyć alokację stosu NMAKE, uruchom narzędzie [polecenia EDITBIN/Stack](../../build/reference/stack.md) z większą opcją stosu:

**polecenia EDITBIN/STACK: rezerwacja NMAKE. EXE**

gdzie *rezerwa* jest liczbą większą niż bieżąca alokacja stosu w NMAKE.
