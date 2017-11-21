---
title: "C3552 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3552
dev_langs: C++
helpviewer_keywords: C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 54526c39a928cc534ba815ef8fda802db85f4020
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3552"></a>C3552 błąd kompilatora
Typ "typename": późne określony typ zwracany nie może zawierać "auto"  
  
 Jeśli używasz `auto` słowa kluczowego jako symbol zastępczy dla zwracanego typu funkcji, należy podać późne określony typ zwracany. Jednak nie można użyć innej `auto` — słowo kluczowe, aby określić późne określonym przez typ zwracany. Na przykład poniższy fragment kodu zwraca błąd C3552.  
  
 `auto myFunction->auto; // C3552`