---
title: Błąd krytyczny C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 6ed70a81c4ae2028d09b694f325f83454e99a587
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203102"
---
# <a name="fatal-error-c1382"></a>Błąd krytyczny C1382

plik PCH "File" został odbudowany od momentu wygenerowania "obj". Skompiluj ponownie ten obiekt

W przypadku korzystania z [/LTCG](../../build/reference/ltcg-link-time-code-generation.md)Kompilator wykrył plik. PCH, który jest NOWSZY niż CIL. obj wskazuje na to. Informacje w pliku CIL. obj są nieaktualne. Skompiluj ponownie obiekt.

C1382 może również wystąpić, Jeśli kompilujesz z **/YC**, ale również przekażesz wiele plików kodu źródłowego do kompilatora.  Aby rozwiązać ten problem, nie należy używać **/YC** podczas przekazywania wielu plików kodu źródłowego do kompilatora.  Aby uzyskać więcej informacji, zobacz [/YC (Create prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md).
