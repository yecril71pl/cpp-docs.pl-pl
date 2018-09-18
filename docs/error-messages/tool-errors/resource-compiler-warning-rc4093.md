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
ms.openlocfilehash: 9b1ca04b17ebdb9d48bc94032482caf48ad4aa00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111566"
---
# <a name="resource-compiler-warning-rc4093"></a>Ostrzeżenie RC4093 kompilatora zasobów

o niezmienionym znaczeniu nowego wiersza w stałej znakowej w nieaktywnego kodu

Wyrażenie stałe `#if`, `#elif`, **#ifdef**, lub **#ifndef** dyrektywy preprocesora, obliczone na wartość 0, dzięki czemu kod jest zgodna nieaktywne. W tym nieaktywnego kodu znaku nowego wiersza pojawiły się w ramach zestawu pojedyncze lub podwójne znaki cudzysłowu.

Cały tekst, aż do następnego podwójny cudzysłów został uznany za w obrębie stałej znaku.