---
title: "C3728 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3728
dev_langs: C++
helpviewer_keywords: C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d20a0772a38dadc5956e1d174a23ecb0a8593647
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3728"></a>C3728 błąd kompilatora
"event": zdarzenie nie posiada metody wzrostu  
  
 Metadane utworzone z językiem, takich jak C#, który nie zezwala na zdarzenie, aby być wywoływane z poza klasą, w którym została zdefiniowana, został uwzględniony [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy i programu Visual C++ przy użyciu próbował CLR — programowanie Wywołaj zdarzenie.  
  
 Aby wywołać zdarzenie w programie w języku, takich jak C#, klasa zawierający zdarzenia musi także definiować metodę publiczną, która wywołuje zdarzenie.