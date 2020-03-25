---
title: Ostrzeżenie RC4093 kompilatora zasobów
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 29d24f1e380f5c531e170e5dc23cf5c77eefb874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182295"
---
# <a name="resource-compiler-warning-rc4093"></a>Ostrzeżenie RC4093 kompilatora zasobów

niezmieniony nowy wiersz w stałej znakowej w nieaktywnym kodzie

Wyrażenie stałe dla dyrektywy preprocesora `#if`, `#elif`, **#ifdef**lub **#ifndef** zostało ocenione jako zero, tworząc kod, który jest nieaktywny. W tym nieaktywnym kodzie, znak nowego wiersza pojawił się w obrębie zestawu pojedynczego lub podwójnego cudzysłowu.

Cały tekst do momentu następnego podwójnego cudzysłowu był traktowany jako jako znak stałej.
