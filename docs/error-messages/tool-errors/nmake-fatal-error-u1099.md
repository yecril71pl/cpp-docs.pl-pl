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
ms.openlocfilehash: 7be09691de4212d07b1452ffe33725a3978fc053
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1099"></a>Błąd krytyczny NMAKE U1099
przepełnienie stosu  
  
 Trwa przetwarzanie pliku reguł programu make było zbyt skomplikowane bieżącej alokacji stosu w NMAKE. NMAKE ma alokacji 0x3000 (12K).  
  
 Aby zwiększyć liczbę alokacji stosu w NMAKE, uruchom [/stack polecenia editbin](../../build/reference/stack.md) narzędzie z opcją większych stosu:  
  
 **polecenia editbin /STACK:reserve NMAKE. WYWOŁANIE PLIKU EXE**  
  
 gdzie *zarezerwować* jest większa niż bieżąca Alokacja stosu w NMAKE liczbą.