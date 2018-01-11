---
title: "Błąd krytyczny kompilatora zasobów RC1018 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC1018
dev_langs: C++
helpviewer_keywords: RC1018
ms.assetid: bb1d2efd-6898-412f-bb03-9ff94c54e4dc
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cbae052efa85c5ee17517363e7a5f38475dbc37e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rc1018"></a>Błąd krytyczny kompilatora zasobów RC1018
Nieoczekiwany #elif  
  
 `#elif` Dyrektywy nie pojawił się w obrębie `#if`, **#ifdef**, lub **#ifndef** utworzenia.  
  
 Upewnij się, że istnieje `#if`, **#ifdef**, lub **#ifndef** instrukcji obowiązywać przed tej instrukcji.