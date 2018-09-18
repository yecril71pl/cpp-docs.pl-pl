---
title: Błąd krytyczny NMAKE U1099 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1099
dev_langs:
- C++
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3ef75a1435d8c922087fcdd21d1941961bc82cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113386"
---
# <a name="nmake-fatal-error-u1099"></a>Błąd krytyczny NMAKE U1099

przepełnienie stosu

Trwa przetwarzanie pliku reguł programu make jest zbyt złożona, bieżący alokacji stosu w NMAKE. NMAKE ma alokacji 0x3000 (12 KB).

Aby zwiększyć alokacji stosu w NMAKE, uruchom [editbin /stack](../../build/reference/stack.md) narzędzia z opcją większej stosu:

**editbin /STACK:reserve NMAKE. PLIK EXE**

gdzie *zarezerwować* jest większa niż bieżąca Alokacja stosu w NMAKE liczbą.