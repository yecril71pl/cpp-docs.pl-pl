---
title: C3554 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3554
dev_langs:
- C++
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fb374e028097157ae72b621593a899af9fe2f91
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255456"
---
# <a name="compiler-error-c3554"></a>C3554 błąd kompilatora
"decltype" nie można łączyć z jakimkolwiek innym specyfikatorem typu  
  
 Nie może kwalifikować `decltype()` — słowo kluczowe z dowolnym specyfikatora typu. Na przykład poniższy fragment kodu zwraca błąd C3554.  
  
```  
int x;  
unsigned decltype(x); // C3554  
```