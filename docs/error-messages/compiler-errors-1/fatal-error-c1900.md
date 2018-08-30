---
title: Błąd krytyczny C1900 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1900
dev_langs:
- C++
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b2211b4243ddf44194959a263fd90ec1a615ea0a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220284"
---
# <a name="fatal-error-c1900"></a>Błąd krytyczny C1900

> Niezgodność IL między "*tool1*"version"*Liczba1*"i"*tool2*"version"*liczba2*"

Narzędzia uruchamiane w różnych przebiegów kompilator nie są zgodne. *Liczba1* i *liczba2* dotyczą daty na plikach. Na przykład w 1. przejścia, kompilator frontonu przebiegów zakończenia (c1.dll) i 2. przejścia, kompilator kopię końcowy uruchomień (c2.dll). Daty w pliki muszą być zgodne.

Aby rozwiązać ten problem, upewnij się, że wszystkie aktualizacje zostały zastosowane do programu Visual Studio. Jeśli problem będzie nadal występować, użyj **programy i funkcje** w Panelu sterowania Windows, aby naprawić lub zainstalować ponownie program Visual Studio.