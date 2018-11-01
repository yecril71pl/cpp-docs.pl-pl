---
title: Błąd krytyczny kompilatora zasobów RC1022
ms.date: 11/04/2016
f1_keywords:
- RC1022
helpviewer_keywords:
- RC1022
ms.assetid: 30a0f3c7-08a8-4c40-b0de-46ee5feb789d
ms.openlocfilehash: 6ee09105822ea7dd4243741ed00ce36978f09583
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540914"
---
# <a name="resource-compiler-fatal-error-rc1022"></a>Błąd krytyczny kompilatora zasobów RC1022

Oczekiwano #endif

`#if`, **#Ifdef**, lub **#ifndef** dyrektywy nie została przerwana z `#endif` dyrektywy.

Upewnij się, że istnieje `#if`, **#ifdef**, lub **#ifndef** instrukcję obowiązywać przed tej instrukcji.