---
title: Błąd krytyczny kompilatora zasobów RC1052
ms.date: 11/04/2016
f1_keywords:
- RC1052
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
ms.openlocfilehash: ad0fe23b20870610c5979d6ad85fce55b4e506d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182559"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Błąd krytyczny kompilatora zasobów RC1052

ograniczenie kompilatora: bloki #if lub #ifdef zagnieżdżone zbyt głęboko

Program przekroczył maksymalną dozwoloną liczbę poziomów zagnieżdżenia dla dyrektyw `#if` i `#ifdef`.

Przyczyną tego błędu może być dołączenie plików, które używają tych dyrektyw preprocesora.

Aby rozwiązać ten problem, zmniejsz liczbę zagnieżdżonych `#if` i dyrektyw `#ifdef` w pliku zasobów. Jeśli problem jest spowodowany przez pliki nagłówkowe, które są zawarte w pliku zasobów, zmniejsz liczbę zagnieżdżonych `#if` i `#ifdef` dyrektyw w plikach nagłówkowych. Jeśli nie jest to możliwe, rozważ utworzenie i uwzględnienie nowego pliku nagłówkowego w pliku zasobów, uruchamiając preprocesor w istniejących plikach nagłówkowych. Aby uzyskać więcej informacji, zobacz opcja kompilatora [/p (preprocess to File)](../../build/reference/p-preprocess-to-a-file.md) .
