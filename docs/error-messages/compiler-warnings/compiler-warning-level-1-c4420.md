---
title: "Kompilatora (poziom 1) ostrzeżenie C4420 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4420
dev_langs: C++
helpviewer_keywords: C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 646e87243e6901827fb2d36076a95e6bcb63c3ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4420"></a>Kompilator C4420 ostrzegawcze (poziom 1)
"operator": operator nie jest dostępny, zamiast 'operator'; Kontrola czasu wykonania może być naruszona  
  
 To ostrzeżenie jest generowany, gdy używasz [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (wektorów sprawdzanie nowych/usuwania) oraz gdy zostanie znaleziony żaden formularz wektora. W takim przypadku formularz-vector jest używany.  
  
 Aby /RTCv działał prawidłowo, kompilator zawsze powinny wywoływać postaci wektorowej [nowe](../../cpp/new-operator-cpp.md)/[usunąć](../../cpp/delete-operator-cpp.md) użycie składni wektora.