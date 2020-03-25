---
title: Błąd kompilatora zasobów RC2144
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: 1b080916642fc1be4b22820668c4cb4137675425
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191200"
---
# <a name="resource-compiler-error-rc2144"></a>Błąd kompilatora zasobów RC2144

Identyfikator języka podstawowego nie jest liczbą

Identyfikator języka podstawowego musi być IDENTYFIKATORem w formacie szesnastkowym. Aby zapoznać się z listą prawidłowych identyfikatorów języka, zobacz [ciągi języka i kraju/regionu](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) w dokumentacji dotyczącej *biblioteki wykonawczej* .

Ten błąd może również wystąpić, jeśli zasoby zostały dodane i usunięte z programu. RC — plik za pomocą narzędzia. Aby rozwiązać ten problem, Otwórz. Plik RC w edytorze tekstów i ręcznie czyści wszystkie nieużywane zasoby.
