---
title: Błąd krytyczny kompilatora zasobów RC1020
ms.date: 11/04/2016
f1_keywords:
- RC1020
helpviewer_keywords:
- RC1020
ms.assetid: 3e073ebf-9136-4bf8-ac6a-3c642ed64594
ms.openlocfilehash: ff4cc5564f59d0adf74ae86149130dd5d017a9ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182685"
---
# <a name="resource-compiler-fatal-error-rc1020"></a>Błąd krytyczny kompilatora zasobów RC1020

Nieoczekiwany element "#endif"

Dyrektywa `#endif` była wyświetlana bez zgodnej dyrektywy `#if`, **#ifdef**lub **#ifndef** .

Upewnij się, że istnieją pasujące `#endif` dla każdej instrukcji `#if`, **#ifdef**i **#ifndef** .
