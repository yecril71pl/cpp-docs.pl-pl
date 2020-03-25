---
title: Błąd krytyczny C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: 6a802928315126b72397ba6e8cc61b66f46deb41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202843"
---
# <a name="fatal-error-c1900"></a>Błąd krytyczny C1900

> Niezgodność Il między "*Tool1*" w wersji "*Liczba1*" i "*Tool2*" w wersji "*liczba2*"

Narzędzia działające w różnych przebiegach kompilatora nie są zgodne. *Liczba1* i *liczba2* zapoznaj się z datami plików. Na przykład w przypadku przebiegu 1 uruchamiane są frontony kompilatora (C1. dll) i w przebiegu 2, uruchomione zaplecza kompilatora (C2. dll). Daty w plikach muszą być zgodne.

Aby rozwiązać ten problem, upewnij się, że wszystkie aktualizacje zostały zastosowane do programu Visual Studio. Jeśli problem nie zniknie, użyj **apletu programy i funkcje** w panelu sterowania systemu Windows, aby naprawić lub ponownie zainstalować program Visual Studio.
