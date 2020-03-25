---
title: Błąd krytyczny C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 106dfe8a078047225097686d185a1ba43987ce33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202633"
---
# <a name="fatal-error-c1905"></a>Błąd krytyczny C1905

Fronton i zaplecze nie są zgodne (muszą dotyczyć tego samego procesora)

Ten błąd występuje, gdy plik. obj jest generowany przez fronton kompilatora (C1. dll), który jest przeznaczony dla jednego procesora, takiego jak x86, ARM lub x64, ale jest odczytywany przez zaplecza (C2. dll), które jest przeznaczone dla innego procesora.

Aby rozwiązać ten problem, upewnij się, że używasz zgodnego frontonu i zaplecza. Jest to wartość domyślna dla projektów utworzonych w programie Visual Studio. Ten błąd może wystąpić, jeśli plik projektu został zmodyfikowany i użyto różnych ścieżek do narzędzi kompilatora. Jeśli nie ustawisz jawnie ścieżki narzędzi kompilatora, ten błąd może wystąpić, jeśli instalacja programu Visual Studio jest uszkodzona. Można na przykład skopiować pliki kompilatora. dll z jednej lokalizacji do innej. Napraw lub ponownie zainstaluj program Visual Studio za pomocą **apletu programy i funkcje** w panelu sterowania systemu Windows.
