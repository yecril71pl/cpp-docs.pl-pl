---
title: 1.1 zakres | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b4f348f55cb956802bab9651b22804c941c53cdb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="11-scope"></a>1.1 Zakres
Określenie tej wartości obejmuje tylko przekierowywany użytkownik paralelizacja, w którym użytkownik jawnie określa akcje podejmowane przez kompilator i środowiska wykonawczego systemu w celu wykonania programu równolegle. Implementacje Openmpc i C++ nie są wymagane do sprawdzenia zależności konflikty, zakleszczenie, wyścigu lub innych problemów, które powoduje wykonanie programu niepoprawne. Użytkownik jest odpowiedzialny za egzekwowanie poprawnie wykonuje aplikacji przy użyciu konstrukcji Openmpc i C++ interfejsu API. W tym dokumencie nie są objęte generowane przez kompilator automatyczna paralelizacja i dyrektywy kompilatora ułatwiających takich paralelizacja.