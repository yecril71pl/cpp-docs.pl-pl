---
title: Błąd krytyczny kompilatora zasobów RC1019
ms.date: 11/04/2016
f1_keywords:
- RC1019
helpviewer_keywords:
- RC1019
ms.assetid: 432fff44-04a9-4e13-91c6-870df6f0b4e4
ms.openlocfilehash: b9f83d9bcacce2e76a0e9deeeddfe21863688552
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297557"
---
# <a name="resource-compiler-fatal-error-rc1019"></a>Błąd krytyczny kompilatora zasobów RC1019

Nieoczekiwany "#else"

`#else` Dyrektywy nie pojawiły się w obrębie `#if`, **#ifdef**, lub **#ifndef** konstruowania.

Upewnij się, że istnieje `#if`, **#ifdef**, lub **#ifndef** instrukcję obowiązywać przed tej instrukcji.