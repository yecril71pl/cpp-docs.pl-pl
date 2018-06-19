---
title: C3728 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae204db616db9e7d7e04cfd62d53374b0793aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273227"
---
# <a name="compiler-error-c3728"></a>C3728 błąd kompilatora
"event": zdarzenie nie posiada metody wzrostu  
  
 Metadane utworzone z językiem, takich jak C#, który nie zezwala na zdarzenie, aby być wywoływane z poza klasą, w którym została zdefiniowana, został uwzględniony [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy i programu Visual C++ przy użyciu próbował CLR — programowanie Wywołaj zdarzenie.  
  
 Aby wywołać zdarzenie w programie w języku, takich jak C#, klasa zawierający zdarzenia musi także definiować metodę publiczną, która wywołuje zdarzenie.