---
title: "Błąd krytyczny NMAKE U1099 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1099
dev_langs: C++
helpviewer_keywords: U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e84cb96fdc8b3abfa118d653162e40c90683447a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1099"></a>Błąd krytyczny NMAKE U1099
przepełnienie stosu  
  
 Trwa przetwarzanie pliku reguł programu make było zbyt skomplikowane bieżącej alokacji stosu w NMAKE. NMAKE ma alokacji 0x3000 (12K).  
  
 Aby zwiększyć liczbę alokacji stosu w NMAKE, uruchom [/stack polecenia editbin](../../build/reference/stack.md) narzędzie z opcją większych stosu:  
  
 **polecenia editbin /STACK:reserve NMAKE. WYWOŁANIE PLIKU EXE**  
  
 gdzie *zarezerwować* jest większa niż bieżąca Alokacja stosu w NMAKE liczbą.