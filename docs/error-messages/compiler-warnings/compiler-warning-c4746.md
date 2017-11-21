---
title: "C4746 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b88f51aa9365c0795c8d3d944ba9f3a8db059d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4746"></a>C4746 ostrzeżenia kompilatora
nietrwały dostęp "\<wyrażenie >" podlega/volatile: [iso &#124; ms] Ustawianie; Rozważ użycie funkcji wewnętrznych __iso_volatile_load/store.  
  
 C4746 jest emitowany zawsze, gdy zmienna volatile jest dostępny bezpośrednio. Ma pomóc deweloperom identyfikują lokalizacje kodu, których dotyczy określonych aktualnie określony model volatile (które można sterować za pomocą [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) — opcja kompilatora). W szczególności może być przydatne w znajdowaniu bariery pamięci sprzętowej generowane przez kompilator, gdy /volatile:ms jest używany.  
  
 Funkcji wewnętrznych __iso_volatile_load/store można jawnie uzyskiwanie dostępu do pamięci volatile bez wpływowi volatile modelu. Przy użyciu tych funkcje wewnętrzne nie powoduje wyzwolenia C4746.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.