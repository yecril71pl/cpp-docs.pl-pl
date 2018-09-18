---
title: Błąd krytyczny kompilatora zasobów RC1052 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1052
dev_langs:
- C++
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef276bdecf675a178f43f22e3aef88f4ed1c73cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071188"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Błąd krytyczny kompilatora zasobów RC1052

ograniczenie kompilatora: bloki #if lub #ifdef są zagnieżdżone zbyt głęboko

Program przekroczył maksymalny dopuszczalny rozmiar poziomów zagnieżdżenia w `#if` i `#ifdef` dyrektywy.

Ten błąd może być spowodowany przez obejmują pliki, które zawiera dyrektywy preprocesora.

Aby rozwiązać ten problem, Zmniejsz liczbę zagnieżdżonych `#if` i `#ifdef` dyrektywy w pliku zasobów. Jeśli ten problem jest spowodowany przez pliki nagłówkowe, które znajdują się w pliku zasobów, Zmniejsz liczbę zagnieżdżonych `#if` i `#ifdef` dyrektywy w plikach nagłówkowych. Jeśli nie jest to możliwe, należy wziąć pod uwagę tworzenia i dołączania nowy plik nagłówkowy w pliku zasobów, uruchamiając polecenie preprocesora do istniejących plików dołączony nagłówek. Aby uzyskać więcej informacji, zobacz [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora.