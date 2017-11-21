---
title: "Błąd krytyczny kompilatora zasobów RC1022 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC1022
dev_langs: C++
helpviewer_keywords: RC1022
ms.assetid: 30a0f3c7-08a8-4c40-b0de-46ee5feb789d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7858f2395b0ef224b557f82a8669c5dab667cd7a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-fatal-error-rc1022"></a>Błąd krytyczny kompilatora zasobów RC1022
Oczekiwano "#endif"  
  
 `#if`, **#Ifdef**, lub **#ifndef** dyrektywy nie zostało zakończone z `#endif` dyrektywy.  
  
 Upewnij się, że istnieje `#if`, **#ifdef**, lub **#ifndef** instrukcji obowiązywać przed tej instrukcji.