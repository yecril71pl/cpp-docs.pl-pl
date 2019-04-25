---
title: Błąd krytyczny C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: c4622dd4552f7bfcc822a3aab4d5783146d68ac7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165726"
---
# <a name="fatal-error-c1900"></a>Błąd krytyczny C1900

> Niezgodność IL między "*tool1*"version"*Liczba1*"i"*tool2*"version"*liczba2*"

Narzędzia uruchamiane w różnych przebiegów kompilator nie są zgodne. *Liczba1* i *liczba2* dotyczą daty na plikach. Na przykład w 1. przejścia, kompilator frontonu przebiegów zakończenia (c1.dll) i 2. przejścia, kompilator kopię końcowy uruchomień (c2.dll). Daty w pliki muszą być zgodne.

Aby rozwiązać ten problem, upewnij się, że wszystkie aktualizacje zostały zastosowane do programu Visual Studio. Jeśli problem będzie nadal występować, użyj **programy i funkcje** w Panelu sterowania Windows, aby naprawić lub zainstalować ponownie program Visual Studio.