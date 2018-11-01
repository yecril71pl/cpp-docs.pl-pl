---
title: Błąd krytyczny kompilatora zasobów RC1052
ms.date: 11/04/2016
f1_keywords:
- RC1052
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
ms.openlocfilehash: 2ab9dd48420ca263abbf3da22da878a3e74a2151
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488416"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Błąd krytyczny kompilatora zasobów RC1052

ograniczenie kompilatora: bloki #if lub #ifdef są zagnieżdżone zbyt głęboko

Program przekroczył maksymalny dopuszczalny rozmiar poziomów zagnieżdżenia w `#if` i `#ifdef` dyrektywy.

Ten błąd może być spowodowany przez obejmują pliki, które zawiera dyrektywy preprocesora.

Aby rozwiązać ten problem, Zmniejsz liczbę zagnieżdżonych `#if` i `#ifdef` dyrektywy w pliku zasobów. Jeśli ten problem jest spowodowany przez pliki nagłówkowe, które znajdują się w pliku zasobów, Zmniejsz liczbę zagnieżdżonych `#if` i `#ifdef` dyrektywy w plikach nagłówkowych. Jeśli nie jest to możliwe, należy wziąć pod uwagę tworzenia i dołączania nowy plik nagłówkowy w pliku zasobów, uruchamiając polecenie preprocesora do istniejących plików dołączony nagłówek. Aby uzyskać więcej informacji, zobacz [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora.