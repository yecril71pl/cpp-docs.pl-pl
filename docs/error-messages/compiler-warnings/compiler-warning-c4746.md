---
title: C4746 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d00c75b2b7cdf2fdafb4e109496a701fb561cb9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4746"></a>C4746 ostrzeżenia kompilatora
nietrwały dostęp "\<wyrażenie >" podlega/volatile: [iso&#124;ms] Ustawianie; Rozważ użycie funkcji wewnętrznych __iso_volatile_load/store.  
  
 C4746 jest emitowany zawsze, gdy zmienna volatile jest dostępny bezpośrednio. Ma pomóc deweloperom identyfikują lokalizacje kodu, których dotyczy określonych aktualnie określony model volatile (które można sterować za pomocą [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) — opcja kompilatora). W szczególności może być przydatne w znajdowaniu bariery pamięci sprzętowej generowane przez kompilator, gdy /volatile:ms jest używany.  
  
 Funkcji wewnętrznych __iso_volatile_load/store można jawnie uzyskiwanie dostępu do pamięci volatile bez wpływowi volatile modelu. Przy użyciu tych funkcje wewnętrzne nie powoduje wyzwolenia C4746.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.