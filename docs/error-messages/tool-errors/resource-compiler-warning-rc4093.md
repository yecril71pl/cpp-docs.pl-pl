---
title: Ostrzeżenie RC4093 kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4093
dev_langs:
- C++
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cca3c2a139e1109746f3a690cfb3f31509a9fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322435"
---
# <a name="resource-compiler-warning-rc4093"></a>Ostrzeżenie RC4093 kompilatora zasobów
niezmienionym znaczeniu nowego wiersza w stałej znakowej w nieaktywnego kodu  
  
 Stałe wyrażenie `#if`, `#elif`, **#ifdef**, lub **#ifndef** dyrektywy preprocesora obliczoną wartością zero, co kod, który wykonuje nieaktywne. W tym nieaktywnego kodu znaku nowego wiersza znajdowały się w ramach zestawu jednej lub podwójny cudzysłów.  
  
 Cały tekst do czasu następnego podwójny cudzysłów został uznany za w stałej znakowej.