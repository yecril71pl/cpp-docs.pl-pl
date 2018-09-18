---
title: Błąd krytyczny kompilatora zasobów RC1019 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1019
dev_langs:
- C++
helpviewer_keywords:
- RC1019
ms.assetid: 432fff44-04a9-4e13-91c6-870df6f0b4e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a455daffba3957b9a4628ecab9e604994e4a4ce2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027092"
---
# <a name="resource-compiler-fatal-error-rc1019"></a>Błąd krytyczny kompilatora zasobów RC1019

Nieoczekiwany "#else"

`#else` Dyrektywy nie pojawiły się w obrębie `#if`, **#ifdef**, lub **#ifndef** konstruowania.

Upewnij się, że istnieje `#if`, **#ifdef**, lub **#ifndef** instrukcję obowiązywać przed tej instrukcji.