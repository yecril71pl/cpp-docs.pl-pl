---
title: "Błąd krytyczny kompilatora zasobów RC1052 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC1052
dev_langs:
- C++
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0546441022d8e2b487d83e291574020665cdaf4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Błąd krytyczny kompilatora zasobów RC1052
ograniczenie kompilatora: bloki #if lub #ifdef są zagnieżdżone zbyt głęboko  
  
 Program przekroczył maksymalny dopuszczalny poziomów zagnieżdżenia w `#if` i `#ifdef` dyrektywy.  
  
 Ten błąd może być spowodowany przez pliki dołączania, które dyrektywy preprocesora.  
  
 Aby rozwiązać ten problem, Zmniejsz liczbę zagnieżdżonych `#if` i `#ifdef` dyrektywy w pliku zasobów. Jeśli przyczyną problemu jest pliki nagłówkowe, które znajdują się w pliku zasobów, Zmniejsz liczbę zagnieżdżonych `#if` i `#ifdef` dyrektywy w pliku nagłówka. Jeśli nie jest to możliwe, należy rozważyć utworzenie i uruchamiając preprocesora na istniejące pliki dołączony nagłówek w tym pliku nagłówka w pliku zasobów. Aby uzyskać więcej informacji, zobacz [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora.