---
title: "Ostrzeżenie RC4005 kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC4005
dev_langs: C++
helpviewer_keywords: RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f27de973f0ff18493c182bdf1feb3f2812f39af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rc4005"></a>Ostrzeżenie RC4005 kompilatora zasobów
"identyfikator": zmiana definicji makra  
  
 Identyfikator jest zdefiniowana dwukrotnie. Kompilator używane druga definicja makra.  
  
 To ostrzeżenie może być spowodowana przez definiowanie makra w wierszu polecenia, a w kodzie z `#define` dyrektywy. On również może być spowodowane makra zaimportowane z plików dołączanych.  
  
 Aby usunąć to ostrzeżenie, usuń jedną z definicji lub użyj `#undef` dyrektywy przed druga definicja.