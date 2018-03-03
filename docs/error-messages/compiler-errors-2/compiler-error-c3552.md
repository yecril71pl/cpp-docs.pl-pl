---
title: "C3552 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca49c6678a147988ee0b2fb0ab57b6883b80539a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3552"></a>C3552 błąd kompilatora
Typ "typename": późne określony typ zwracany nie może zawierać "auto"  
  
 Jeśli używasz `auto` słowa kluczowego jako symbol zastępczy dla zwracanego typu funkcji, należy podać późne określony typ zwracany. Jednak nie można użyć innej `auto` — słowo kluczowe, aby określić późne określonym przez typ zwracany. Na przykład poniższy fragment kodu zwraca błąd C3552.  
  
 `auto myFunction->auto; // C3552`