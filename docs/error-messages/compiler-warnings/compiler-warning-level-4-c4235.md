---
title: "Kompilatora (poziom 4) ostrzeżenie C4235 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4235
dev_langs: C++
helpviewer_keywords: C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f4266a2aae53254bbb7c2a043ccf3240d69cc63a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4235"></a>Kompilator C4235 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: słowo kluczowe "— słowo kluczowe" nie jest obsługiwane w tej architekturze  
  
 Kompilator nie obsługuje słowa kluczowego użytym.  
  
 To ostrzeżenie zostanie automatycznie podwyższony do wystąpił błąd. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład aby C4235 do ostrzeżenia poziomu 2, należy użyć następującego kodu  
  
```  
#pragma warning(2:4235)  
```  
  
 w pliku kodu źródłowego.