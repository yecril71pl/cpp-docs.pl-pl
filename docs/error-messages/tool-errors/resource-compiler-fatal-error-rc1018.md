---
title: Błąd krytyczny kompilatora zasobów RC1018
ms.date: 11/04/2016
f1_keywords:
- RC1018
helpviewer_keywords:
- RC1018
ms.assetid: bb1d2efd-6898-412f-bb03-9ff94c54e4dc
ms.openlocfilehash: 02e37ae2f48a6d87da128078d0e18a76f400817f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666586"
---
# <a name="resource-compiler-fatal-error-rc1018"></a>Błąd krytyczny kompilatora zasobów RC1018

Nieoczekiwany #elif

`#elif` Dyrektywy nie pojawiły się w obrębie `#if`, **#ifdef**, lub **#ifndef** konstruowania.

Upewnij się, że istnieje `#if`, **#ifdef**, lub **#ifndef** instrukcję obowiązywać przed tej instrukcji.