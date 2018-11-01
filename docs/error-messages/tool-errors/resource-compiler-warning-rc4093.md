---
title: Ostrzeżenie RC4093 kompilatora zasobów
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 23bf436e6e8338f89bc576564181c84715028332
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541885"
---
# <a name="resource-compiler-warning-rc4093"></a>Ostrzeżenie RC4093 kompilatora zasobów

o niezmienionym znaczeniu nowego wiersza w stałej znakowej w nieaktywnego kodu

Wyrażenie stałe `#if`, `#elif`, **#ifdef**, lub **#ifndef** dyrektywy preprocesora, obliczone na wartość 0, dzięki czemu kod jest zgodna nieaktywne. W tym nieaktywnego kodu znaku nowego wiersza pojawiły się w ramach zestawu pojedyncze lub podwójne znaki cudzysłowu.

Cały tekst, aż do następnego podwójny cudzysłów został uznany za w obrębie stałej znaku.