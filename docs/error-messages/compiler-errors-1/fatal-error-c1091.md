---
title: Błąd krytyczny C1091
ms.date: 11/04/2016
f1_keywords:
- C1091
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
ms.openlocfilehash: 76492be7abab6deb740f1670b85274b8c296c783
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203895"
---
# <a name="fatal-error-c1091"></a>Błąd krytyczny C1091

ograniczenie kompilatora: ciąg przekracza długość (w bajtach)

Stała ciągu przekracza bieżący limit długości ciągów.

Możesz chcieć podzielić ciąg statyczny na dwie zmienne (lub więcej) i użyć [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) , aby dołączyć wynik jako część deklaracji lub w czasie wykonywania.
