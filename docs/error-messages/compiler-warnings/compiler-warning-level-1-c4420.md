---
title: Kompilatora (poziom 1) ostrzeżenie C4420 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4420
dev_langs:
- C++
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98336a30e7174b62df48e93a04ba9ee7ddcc919a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4420"></a>Kompilator C4420 ostrzegawcze (poziom 1)
"operator": operator nie jest dostępny, zamiast 'operator'; Kontrola czasu wykonania może być naruszona  
  
 To ostrzeżenie jest generowany, gdy używasz [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (wektorów sprawdzanie nowych/usuwania) oraz gdy zostanie znaleziony żaden formularz wektora. W takim przypadku formularz-vector jest używany.  
  
 Aby /RTCv działał prawidłowo, kompilator zawsze powinny wywoływać postaci wektorowej [nowe](../../cpp/new-operator-cpp.md)/[usunąć](../../cpp/delete-operator-cpp.md) użycie składni wektora.