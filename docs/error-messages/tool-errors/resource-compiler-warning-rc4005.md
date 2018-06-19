---
title: Ostrzeżenie RC4005 kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 724764e443d4ab999c1df1247e9f5572ebdb2078
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322487"
---
# <a name="resource-compiler-warning-rc4005"></a>Ostrzeżenie RC4005 kompilatora zasobów
"identyfikator": zmiana definicji makra  
  
 Identyfikator jest zdefiniowana dwukrotnie. Kompilator używane druga definicja makra.  
  
 To ostrzeżenie może być spowodowana przez definiowanie makra w wierszu polecenia, a w kodzie z `#define` dyrektywy. On również może być spowodowane makra zaimportowane z plików dołączanych.  
  
 Aby usunąć to ostrzeżenie, usuń jedną z definicji lub użyj `#undef` dyrektywy przed druga definicja.